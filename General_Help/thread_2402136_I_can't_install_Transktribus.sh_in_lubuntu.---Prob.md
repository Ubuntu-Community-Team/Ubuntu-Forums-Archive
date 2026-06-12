---
title: "I can't install Transktribus.sh in lubuntu.---Problem with Java"
date: 2018-09-26
forum: General Help
---

### Post by jdsalasc on 2018-09-26
HI. Please help me :D

I'm trying install Trankstribus.sh  in my lubuntu but went I doing it, the process failed. That is the error:


```
./Transkribus.sh
Starting Transkribus - first trying to find java, your OS = linux-gnu
Found java executable in PATH
Java bin = java
Java version >= 1.7 required!

noodle@noodle-E200HA:~/Documentos/transkripter/Transkribus-1.4.2$ java -jar Transkribus-1.4.2.jar
08:06:36,172 |-INFO in ch.qos.logback.classic.LoggerContext[default] - Could NOT find resource [logback-test.xml]
08:06:36,176 |-INFO in ch.qos.logback.classic.LoggerContext[default] - Could NOT find resource [logback.groovy]
08:06:36,179 |-INFO in ch.qos.logback.classic.LoggerContext[default] - Found resource [logback.xml] at [jar:file:/home/noodle/Documentos/transkripter/Transkribus-1.4.2/Transkribus-1.4.2.jar!/logback.xml]
08:06:36,235 |-INFO in ch.qos.logback.core.joran.spi.ConfigurationWatchList@77888435 - URL [jar:file:/home/noodle/Documentos/transkripter/Transkribus-1.4.2/Transkribus-1.4.2.jar!/logback.xml] is not of type file
08:06:36,729 |-INFO in ch.qos.logback.classic.joran.action.ConfigurationAction - debug attribute not set
08:06:36,732 |-INFO in ch.qos.logback.core.joran.action.AppenderAction - About to instantiate appender of type [ch.qos.logback.core.ConsoleAppender]
08:06:36,755 |-INFO in ch.qos.logback.core.joran.action.AppenderAction - Naming appender as [CONSOLE]
08:06:36,780 |-INFO in ch.qos.logback.core.joran.action.NestedComplexPropertyIA - Assuming default type [ch.qos.logback.classic.encoder.PatternLayoutEncoder] for [encoder] property
08:06:37,097 |-INFO in ch.qos.logback.core.joran.action.AppenderAction - About to instantiate appender of type [ch.qos.logback.core.rolling.RollingFileAppender]
08:06:37,123 |-INFO in ch.qos.logback.core.joran.action.AppenderAction - Naming appender as [LOGFILE]
08:06:37,129 |-INFO in ch.qos.logback.core.joran.action.NestedComplexPropertyIA - Assuming default type [ch.qos.logback.classic.encoder.PatternLayoutEncoder] for [encoder] property
08:06:37,151 |-INFO in c.q.l.core.rolling.TimeBasedRollingPolicy@1939990953 - No compression will be used
08:06:37,155 |-INFO in c.q.l.core.rolling.TimeBasedRollingPolicy@1939990953 - Will use the pattern logs/TrpGui.log.%d{.yyyy-MM} for the active file
08:06:37,167 |-INFO in c.q.l.core.rolling.DefaultTimeBasedFileNamingAndTriggeringPolicy - The date pattern is '.yyyy-MM' from file name pattern 'logs/TrpGui.log.%d{.yyyy-MM}'.
08:06:37,167 |-INFO in c.q.l.core.rolling.DefaultTimeBasedFileNamingAndTriggeringPolicy - Rollover at start of every month.
08:06:37,187 |-INFO in c.q.l.core.rolling.DefaultTimeBasedFileNamingAndTriggeringPolicy - Setting initial period to Tue Sep 25 17:23:48 COT 2018
08:06:37,202 |-INFO in ch.qos.logback.core.rolling.RollingFileAppender[LOGFILE] - Active log file name: logs/TrpGui.log
08:06:37,202 |-INFO in ch.qos.logback.core.rolling.RollingFileAppender[LOGFILE] - File property is set to [logs/TrpGui.log]
08:06:37,205 |-ERROR in ch.qos.logback.core.rolling.RollingFileAppender[LOGFILE] - openFile(logs/TrpGui.log,true) call failed. java.io.FileNotFoundException: logs/TrpGui.log (Permiso denegado)
    at java.io.FileNotFoundException: logs/TrpGui.log (Permiso denegado)
    at     at java.base/java.io.FileOutputStream.open0(Native Method)
    at     at java.base/java.io.FileOutputStream.open(FileOutputStream.java:299)
    at     at java.base/java.io.FileOutputStream.<init>(FileOutputStream.java:238)
    at     at ch.qos.logback.core.recovery.ResilientFileOutputStream.<init>(ResilientFileOutputStream.java:26)
    at     at ch.qos.logback.core.FileAppender.openFile(FileAppender.java:204)
    at     at ch.qos.logback.core.FileAppender.start(FileAppender.java:127)
    at     at ch.qos.logback.core.rolling.RollingFileAppender.start(RollingFileAppender.java:100)
    at     at ch.qos.logback.core.joran.action.AppenderAction.end(AppenderAction.java:90)
    at     at ch.qos.logback.core.joran.spi.Interpreter.callEndAction(Interpreter.java:309)
    at     at ch.qos.logback.core.joran.spi.Interpreter.endElement(Interpreter.java:193)
    at     at ch.qos.logback.core.joran.spi.Interpreter.endElement(Interpreter.java:179)
    at     at ch.qos.logback.core.joran.spi.EventPlayer.play(EventPlayer.java:62)
    at     at ch.qos.logback.core.joran.GenericConfigurator.doConfigure(GenericConfigurator.java:165)
    at     at ch.qos.logback.core.joran.GenericConfigurator.doConfigure(GenericConfigurator.java:152)
    at     at ch.qos.logback.core.joran.GenericConfigurator.doConfigure(GenericConfigurator.java:110)
    at     at ch.qos.logback.core.joran.GenericConfigurator.doConfigure(GenericConfigurator.java:53)
    at     at ch.qos.logback.classic.util.ContextInitializer.configureByResource(ContextInitializer.java:75)
    at     at ch.qos.logback.classic.util.ContextInitializer.autoConfig(ContextInitializer.java:150)
    at     at org.slf4j.impl.StaticLoggerBinder.init(StaticLoggerBinder.java:84)
    at     at org.slf4j.impl.StaticLoggerBinder.<clinit>(StaticLoggerBinder.java:55)
    at     at org.slf4j.LoggerFactory.bind(LoggerFactory.java:150)
    at     at org.slf4j.LoggerFactory.performInitialization(LoggerFactory.java:124)
    at     at org.slf4j.LoggerFactory.getILoggerFactory(LoggerFactory.java:412)
    at     at org.slf4j.LoggerFactory.getLogger(LoggerFactory.java:357)
    at     at org.slf4j.LoggerFactory.getLogger(LoggerFactory.java:383)
    at     at eu.transkribus.swt_gui.TrpGui.<clinit>(TrpGui.java:20)
08:06:37,206 |-INFO in ch.qos.logback.classic.joran.action.LoggerAction - Setting level of logger [eu.transkribus] to INFO
08:06:37,207 |-INFO in ch.qos.logback.core.joran.action.AppenderRefAction - Attaching appender named [CONSOLE] to Logger[eu.transkribus]
08:06:37,208 |-INFO in ch.qos.logback.core.joran.action.AppenderRefAction - Attaching appender named [LOGFILE] to Logger[eu.transkribus]
08:06:37,209 |-INFO in ch.qos.logback.classic.joran.action.LoggerAction - Setting level of logger [org.dea] to INFO
08:06:37,209 |-INFO in ch.qos.logback.core.joran.action.AppenderRefAction - Attaching appender named [CONSOLE] to Logger[org.dea]
08:06:37,209 |-INFO in ch.qos.logback.core.joran.action.AppenderRefAction - Attaching appender named [LOGFILE] to Logger[org.dea]
08:06:37,209 |-INFO in ch.qos.logback.classic.joran.action.LoggerAction - Setting level of logger [org.eclipse] to INFO
08:06:37,209 |-INFO in ch.qos.logback.core.joran.action.AppenderRefAction - Attaching appender named [CONSOLE] to Logger[org.eclipse]
08:06:37,209 |-INFO in ch.qos.logback.core.joran.action.AppenderRefAction - Attaching appender named [LOGFILE] to Logger[org.eclipse]
08:06:37,209 |-INFO in ch.qos.logback.classic.joran.action.LoggerAction - Setting level of logger [org.apache] to ERROR
08:06:37,210 |-INFO in ch.qos.logback.core.joran.action.AppenderRefAction - Attaching appender named [CONSOLE] to Logger[org.apache]
08:06:37,210 |-INFO in ch.qos.logback.core.joran.action.AppenderRefAction - Attaching appender named [LOGFILE] to Logger[org.apache]
08:06:37,210 |-INFO in ch.qos.logback.classic.joran.action.ConfigurationAction - End of configuration.
08:06:37,212 |-INFO in ch.qos.logback.classic.joran.JoranConfigurator@65fb9ffc - Registering current configuration as safe fallback point

08:06:37.234 INFO  [main] eu.transkribus.swt_gui.TrpGui - N swtJars = 1
08:06:37.243 INFO  [main] eu.transkribus.swt_gui.TrpGui - swt jar: swt-4.7.1-linux64.jar
java.lang.ClassCastException: java.base/jdk.internal.loader.ClassLoaders$AppClassLoader cannot be cast to java.base/java.net.URLClassLoader
    at eu.transkribus.util.Utils.addJarToClasspath(Utils.java:200)
    at eu.transkribus.swt_gui.TrpGui.main(TrpGui.java:96)
Exception in thread "main" java.lang.NoClassDefFoundError: org/eclipse/swt/widgets/Listener
    at eu.transkribus.swt_gui.TrpGui.main(TrpGui.java:98)
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.widgets.Listener
    at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:582)
    at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:190)
    at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:499)
    ... 1 more


```


My version of java is 

```

noodle@noodle-E200HA:~/Documentos/transkripter/Transkribus-1.4.2$ java -version -bash
openjdk version "10.0.2" 2018-07-17
OpenJDK Runtime Environment (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.2)
OpenJDK 64-Bit Server VM (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.2, mixed mode)
```

---

### Post by distortedecho on 2018-09-26
From Transkribus's wiki, it says that from 17.04 you need to install:

> sudo apt install libwebkitgtk-1.0-0

Install JAVA from here:

> [https://java.com/en/download/help/linux_install.xml](https://java.com/en/download/help/linux_install.xml)

---

### Post by slickymaster on 2018-09-26
Thread moved to **General Help** for a better fit

---

### Post by jdsalasc on 2018-09-26
First, thanks you

I made that, but the problem continue

---

### Post by aethralis on 2018-10-18
First you have to unistall the current version of java (openjdk 11 or openjdk-default or whatever you have installed). The you have to install openjdk 8 only, and with this version Transkribus works (for me on Ubuntu 18.04).

---

