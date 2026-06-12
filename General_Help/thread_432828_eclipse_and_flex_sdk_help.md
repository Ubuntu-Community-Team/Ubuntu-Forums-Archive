---
title: "eclipse and flex sdk help"
date: 2007-05-04
forum: General Help
---

### Post by ubiwankanubi on 2007-05-04
I'm trying to install eclispe and the flex sdk but I'm running into some trouble.
eclipse installs fine from the repositories, but the flex sdk requires jdk.
so I downloaded the latest jdk from sun and installed it to opt.
then in a terminal i typed export JAVA_HOME="/opt/jdk1.6.0_01"
after that I extracted the flexsdk to /opt/flex_sdk_2
then I went to samples and ran the build samples.sh

while the script is running, i keep getting a segmentation fault such and errors as these:
Segmentation fault (core dumped)
building containers/DividedBoxExample.mxml

Error: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit

java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at flash.graphics.images.ImageUtil.getImage(ImageUtil.java:28)
   at flash.graphics.images.LosslessImage.<init>(LosslessImage.java:31)
   at flex2.compiler.media.LosslessImageTranscoder.getImage(LosslessImageTranscoder.java:30)
   at flex2.compiler.media.ImageTranscoder.doTranscode(ImageTranscoder.java:46)
   at flex2.compiler.media.AbstractTranscoder.transcode(AbstractTranscoder.java:126)
   at flex2.compiler.as3.EmbedUtil.transcode(EmbedUtil.java:184)
   at flex2.compiler.as3.EmbedUtil.transcode(EmbedUtil.java:93)
   at flex2.compiler.as3.EmbedEvaluator.generateSource(EmbedEvaluator.java:292)
   at flex2.compiler.as3.EmbedEvaluator.generateSources(EmbedEvaluator.java:361)
   at flex2.compiler.as3.EmbedEvaluator.evaluate(EmbedEvaluator.java:81)
   at macromedia.asc.parser.ClassDefinitionNode.evaluate(ClassDefinitionNode.java:86)
   at flash.swf.tools.as3.EvaluatorAdapter.evaluate(EvaluatorAdapter.java:330)
   at macromedia.asc.parser.StatementListNode.evaluate(StatementListNode.java:36)
   at flash.swf.tools.as3.EvaluatorAdapter.evaluate(EvaluatorAdapter.java:910)
   at flex2.compiler.as3.EmbedEvaluator.evaluate(EmbedEvaluator.java:269)
   at macromedia.asc.parser.ProgramNode.evaluate(ProgramNode.java:63)
   at flex2.compiler.as3.EmbedExtension.parse1(EmbedExtension.java:39)
   at flex2.compiler.as3.Compiler.parse1(Compiler.java:339)
   at flex2.compiler.mxml.ImplementationCompiler.parse1(ImplementationCompiler.java:153)
   at flex2.compiler.mxml.Compiler.parse1(Compiler.java:100)
   at flex2.compiler.API.parse1(API.java:2158)
   at flex2.compiler.API.parse1(API.java:2111)
   at flex2.compiler.API.batch2(API.java:319)
   at flex2.compiler.API.batch(API.java:1025)
   at flex2.compiler.API.compile(API.java:1211)
   at flex2.compiler.API.compile(API.java:1114)
   at flex2.tools.Compiler.main(Compiler.java:222)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...27 more


has anyone installed the flex sdk on ubuntu? how did you do it?

---

### Post by ubiwankanubi on 2007-05-04
i found this:

[http://renaun.com/blog/2006/12/06/164/](http://renaun.com/blog/2006/12/06/164/)


but when I try to use ant in eclipse or in the terminal I get an error:

<terminated, exit value: 0>/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/bin/java (May 4, 2007 11:12:13 AM)	

how can i get ant to look in /opt/jdk1.6.0_01/lib ? I think this is changing the path or something... but how can i set this permanently?

---

