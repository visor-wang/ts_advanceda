# ts高级特性
## classOf
## keyof
* 取 interface 的键
## Condition Type
* T extends U ? X : Y
## typeof
* const b: typeof a = 4 typeof 代表取某个值的 type
## is:
* 判定值的类型
## infer

## ArrayLike
* 将类型转为类数组的类型，具有number类型的length

## Partial
将类型定义中的所有属性变为可选属性
## Required
将所有的可选类型变为必须类型
## Readonly
将所有的属性转化为只读属性Readonly<T>
## Pick
Pick<IA, 'x' | 'y'>  从IA中取出属性'x' 和 'y'
## Record
Record<Z, IAr> 将Z中的属性全部转为IAr类型
## Exclude
Exclude<D, C> 从D中 取出C中没有的属性
## Extract
Extract<D, C> 去除D，C中共有的属性
## Omit
Omit<IB, C> 从IB中剔除C中的属性
## NonNullable
NonNullable<T> 如果T是null或者undefined返回never，否则返回T
## ReturnType
获取函数的返回类型
## Mutable：
## Proxify


# 自己也写了几个类型函数体验一下

属性拓展
在T上新增类型为Z的K属性,可以拓展多个属性，但属性的类型必须唯一
`declare type Expand<T, K, Z> = {
  [P in (keyof T | K)]: P extends keyof T ? T[P] : Z;
};`

// 属性替换
// 将T中的K属性替换为Z属性，类型不变
`declare type Rename<T, K, Z> = Omit<Expand<T, Z, T[K]>, K>`

// 类型合并
// 将两个接口的属性合并到一个接口中
```
declare type Merge<T, K> = {
  [P in (keyof T | keyof K)]: P extends keyof T ? T[P] : K[P];
}

```