# 企业 Maven 依赖管理层次结构设计

博客上有过几篇 [Maven](https://blog.csdn.net/isea533/category_6992448.html) 方面的文章，涉及到了几个零散的点。这篇 Chat 会专门介绍一个良好的企业级 Maven 依赖管理应该如何设计。内容包含私服配置，第三方依赖管理，公司内部依赖管理，项目结构对应的依赖管理。最后也想通过本篇 Chat 和大家交流一下 Maven 依赖管理方面的经验。

由于本文涉及内容太多，不想在文章中包含太多基础的内容，但是对于了解不深的人来说，没有这些内容也不容易真正掌握，因此在博客上通过 [企业 Maven 依赖管理层次结构设计 - 附录](https://liuzh.blog.csdn.net/article/details/104110775) 补充一些额外的内容来完善本 Chat。*建议在阅读本文前，快速浏览一遍该博客。*

在 Maven 中，存在下面三种依赖：

-  一方库：本工程中各个模块之间的依赖

- 二方库：企业内部的依赖库，一般指企业内部的其他项目发布的依赖（jar 包）

- 三方库：企业之外的第三方依赖库， 如 spring、apache、google 等发布的依赖（jar 包）

本文的层次结构就是为了方便管理**二方库**和**三方库**设计的。一般来说，企业的开发框架搭建完成后，**三方库**依赖除了漏洞和BUG升级外，很少频繁升级大改，而企业内部的**二方库**由于迭代和更新，版本升级频率较**三方库**要高，所以本文的层次结构中**二方库依赖三方库**，**三方库**在更底层。先控制**三方库**依赖版本，在此基础上再控制**二方库**的版本。下面先从基础准备工作开始。

> 本文对应代码和配置：[https://github.com/guozilanTK/company-nexus](https://github.com/guozilanTK/company-nexus)

## 全文地址

https://gitbook.cn/gitchat/activity/5e10b5812a3a513b4f607934

## demos 目录下面是文章相关的几个示例
