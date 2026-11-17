# 五笔词库

整理多个词库得到的五笔码表。目前只支持**五笔 86 版**，不支持五笔 98 或其他编码方案。

## 文件格式

[`wubi86.tsv`](wubi86.tsv) 使用 UTF-8 编码，每行一条，列之间用制表符分隔：

```text
编码<TAB>词或字<TAB>权重
```

编码为 1～4 个小写字母 `a`～`y`。词条按编码排序，同编码下按权重从高到低排列；相同编码和词语的条目已去重。同一个字词可以保留多个编码。词频是合并时用于排序的近似权重，不代表统一来源的真实使用频率。

当前版本包含 935,721 条编码词条。例如，`ygwd` 可匹配“评估”“评优”“语段”等 11 条。

## 在 WowType 中使用

这个 TSV 符合 WowType 的五笔码表格式。macOS 版当前从应用包的 `Contents/Resources/wubi86.tsv` 读取五笔码表；设置界面的“自定义词库”是拼音词库入口，不能用来替换五笔码表。直接修改应用包可能使签名失效，且更新应用后会被覆盖，请按照使用版本的安装和签名要求操作。

## 数据来源

本词库合并、去重或参考了以下项目和数据：

- [Rime 五笔字型 rime-wubi](https://github.com/rime/rime-wubi)：原始 `wubi86.dict.yaml`，采用项目 [WowType 的转换规则](https://github.com/Gloridust/WowType/blob/main/tools/wubi2tsv.py)。所用原文件对应 rime-wubi 提交 `152a0d3f3efe40cae216d1e3b338242446848d07`。该来源标注为 LGPL-3.0，详见其仓库中的许可及作者说明。
- [rime-wubi-dict](https://github.com/xianghongai/rime-wubi-dict)，提交 `1e6afaaa8c7bd605b604d9dc1314d496a8220b92`：单字、词语、成语及分类词库。其 README 称部分词语和成语来自汉典。
- [Wubi](https://github.com/wangdetao8341/Wubi)，提交 `f9877ea2743ca77eb780327c1aa614524da269c4`：五笔 86 文本、分拆码表和可解析的二进制码表。
- [lexicon](https://github.com/skrik2/lexicon)，提交 `3ed738ab8e0db9f659de782f65c060d9d5199bdb`：五笔 86 单字码表及各分类词库；根据单字码按五笔 86 规则生成可编码词组。其 README 参考了百度、搜狗及清华开放词库等来源。
- [WowType](https://github.com/Gloridust/WowType)：提供码表格式和转换工具；合并时对新增词条参考了本地 WowType 拼音词库中的部分词频。

合并时保留已有码表的权重；新增词条有可用词频时借用词频，没有时使用默认权重。无法生成有效五笔编码、含不兼容字符或使用 `z` 编码的条目未收录。部分单字可能有多个来源的不同编码；本项目保留不同的有效编码，候选数量和排序可能与其他输入法不同。

## 许可与使用范围

仓库中的 [LICENSE](LICENSE) 是 Apache-2.0 许可证文本，**不代表它自动适用于 `wubi86.tsv` 中的全部第三方数据**，也不覆盖第三方来源的其他许可要求。

rime-wubi 来源标注 LGPL-3.0；Wubi、rime-wubi-dict 和 lexicon 中相关数据的完整权利归属及再分发授权尚未逐项核实。**因此目前不能确认整份合并词库可按开源许可再分发，也不能将其作为 Apache-2.0 词库使用。** 在公开发布、镜像、商业使用或向其他人提供前，请先核实各来源及其上游的授权，并满足适用的署名、许可文本和其他要求。
