AutoPOI (Excel和 Word简易工具类)
===========================

AutoPOI 功能如同名字auto，追求的就是自动化，让一个没接触过poi的人员，可以傻瓜化的快速实现Excel导入导出、Word模板导出、可以仅仅5行代码就可以完成Excel的导入导出。

> **本仓库是 fork 自 [org.jeecgframework:autopoi](https://github.com/zhangdaiscott/autopoi)（官方最新 1.4.6，Apache License 2.0）的修改版**，
> Maven 坐标为 `io.github.zhangjzz:autopoi(-web):2.0`，与官方版本完全独立，不存在版本混淆。

当前版本： **2.0**

---------------------------
与官方 1.4.6 相比，本 fork 的全部修改
--------------------------

以下内容取自本仓库 git 提交记录（基线：官方 `90742aa 更新到最新版本1.4.6`）：

**功能增强**

| 提交 | 说明 |
|------|------|
| `1928028` | 按注解给定比例缩放图片并导出 |
| `1c246e5` / `5ee7ba7` | 调整图片为比例缩放 |
| `509a0d9` / `b0e2768` | 增加子列表循环列支持 |
| `06bc9ca` / `8edc147` / `adc6dbd` | 模板导出增加可以导出图片（ImageEntity 类）；调整表格导出图片位置 |
| `d681dae` | 修复数据导出数值格式变为字符串格式问题 |

**Jakarta EE / Spring 6 适配（2.0 主线改动）**

- `javax.servlet.*` 全量迁移为 `jakarta.servlet.*`（autopoi-web 5 个 AbstractView 实现：JeecgEntityExcelView / JeecgMapExcelView / JeecgTemplateExcelView / JeecgTemplateWordView / MiniAbstractExcelView）
- servlet-api 2.5 → `jakarta.servlet-api 6.1.0`（provided/optional）
- Spring 5.1.0 → `Spring 6.2.19`
- 编译目标 1.8 → **17**（Spring 6 的最低要求），运行环境建议 JDK 17/21
- 适用场景：Spring Boot 3.x / Jakarta EE 9+ / JDK 17+ 项目；老项目（Spring Boot 2.x）请继续使用官方 1.4.6

---------------------------
AutoPOI的主要特点
--------------------------
	1.设计精巧,使用简单
	2.接口丰富,扩展简单
	3.默认值多,write less do more
	4.AbstractView 支持,web导出可以简单明了

---------------------------
AutoPOI的几个入口工具类
---------------------------

	1.ExcelExportUtil Excel导出(普通导出,模板导出)
	2.ExcelImportUtil Excel导入
	3.WordExportUtil  Word导出(只支持docx ,doc版本poi存在图片的bug,暂不支持)

---------------------------
关于Excel导出XLS和XLSX区别
---------------------------

	1.导出时间XLS比XLSX快2-3倍
	2.导出大小XLS是XLSX的2-3倍或者更多
	3.导出需要综合网速和本地速度做考虑^~^

---------------------------
几个工程的说明
---------------------------
	1.autopoi-parent 父包--作用大家都懂得
	2.autopoi 导入导出的工具包,可以完成Excel导出,导入,Word的导出,Excel的导出功能
	3.autopoi-web  耦合了spring-mvc 基于AbstractView,极大的简化spring-mvc下的导出功能
	4.sax 导入使用xercesImpl这个包(这个包可能造成奇怪的问题哈),word导出使用poi-scratchpad,都作为可选包了

--------------------------
maven
--------------------------

```xml
<dependency>
    <groupId>io.github.zhangjzz</groupId>
    <artifactId>autopoi</artifactId>
    <version>2.0</version>
</dependency>
<!-- Spring MVC 场景 -->
<dependency>
    <groupId>io.github.zhangjzz</groupId>
    <artifactId>autopoi-web</artifactId>
    <version>2.0</version>
</dependency>
```

--------------------------
许可证与致谢
--------------------------

- 本项目基于官方 [AutoPOI](https://github.com/zhangdaiscott/autopoi) 修改，遵循 **Apache License 2.0** 开源，原版权与许可证声明予以保留。
- 感谢 jeecg 官方团队的优秀基础工作。本仓库与其官方版本无任何背书关系。
