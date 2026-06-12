---
title: "Cannot Start CPLEX Studio on Ubuntu Linux"
date: 2013-10-18
forum: General Help
---

### Post by akm3 on 2013-10-18
Hi, I have installed CPLEX ("IBM ILOG CPLEX Optimization Studio Multiplatform Multilingual eAssembly") on a 64-bit Ubuntu Linux 12.04
 
The installation has been successful and I can run cplex interactively inside my terminal.
But I cannot run cplex studio, when I attempt to run:

```
$ /opt/ibm/ILOG/CPLEX_Studio1251/opl/oplide/oplide
```

I get the following error:

```
An error has occurred. See the log file
/opt/ibm/ILOG/CPLEX_Studio1251/opl/oplide/configuration/1382124964123.log.
```

I have attached the log file, and I believe I have to change something in my config.ini file but I am not sure which part, that file is also attached for further reference.


Log:
```
!SESSION 2013-10-18 14:43:12.512 -----------------------------------------------
eclipse.buildId=Build 0
java.fullversion=JRE 1.6.0 IBM J9 2.4 Linux amd64-64 jvmxa6460sr13-20130114_134867 (JIT enabled, AOT enabled)
J9VM - 20130114_134867
JIT  - r9_20130108_31100
GC   - 20121212_AA
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64 -clean

!ENTRY org.eclipse.osgi 4 0 2013-10-18 14:43:13.125
!MESSAGE Bundle org.eclipse.update.configurator@3:start not found.

!ENTRY org.eclipse.equinox.ds 4 0 2013-10-18 14:43:13.199
!MESSAGE 
!STACK 0
org.osgi.framework.BundleException: The bundle "org.eclipse.equinox.ds_1.2.1.R36x_v20100803 [3]" could not be resolved. Reason: Missing Constraint: Import-Package: org.eclipse.equinox.internal.util.event; version="1.0.0"
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.getResolverError(AbstractBundle.java:1317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.getResolutionFailureException(AbstractBundle.java:1301)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:319)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:374)
	at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:1067)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(StartLevelManager.java:561)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(StartLevelManager.java:546)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(StartLevelManager.java:459)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(StartLevelManager.java:243)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:440)
	at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:227)
	at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run(EventManager.java:337)

!ENTRY org.eclipse.core.runtime 4 0 2013-10-18 14:43:13.204
!MESSAGE 
!STACK 0
org.osgi.framework.BundleException: The bundle "org.eclipse.core.runtime_3.6.0.v20100505 [2]" could not be resolved. Reason: Missing Constraint: Require-Bundle: org.eclipse.core.jobs; bundle-version="[3.2.0,4.0.0)"
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.getResolverError(AbstractBundle.java:1317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.getResolutionFailureException(AbstractBundle.java:1301)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:319)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:374)
	at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:1067)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(StartLevelManager.java:561)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(StartLevelManager.java:546)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(StartLevelManager.java:459)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(StartLevelManager.java:243)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:440)
	at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:227)
	at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run(EventManager.java:337)

!ENTRY org.eclipse.osgi 4 0 2013-10-18 14:43:13.204
!MESSAGE Bundle initial@reference:file:plugins/org.eclipse.core.runtime_3.6.0.v20100505.jar/ was not resolved.

!ENTRY org.eclipse.osgi 4 0 2013-10-18 14:43:13.205
!MESSAGE Bundle initial@reference:file:plugins/org.eclipse.equinox.ds_1.2.1.R36x_v20100803.jar/ was not resolved.

!ENTRY org.eclipse.osgi 2 0 2013-10-18 14:43:13.220
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-10-18 14:43:13.220
!MESSAGE Bundle initial@reference:file:plugins/org.eclipse.core.runtime_3.6.0.v20100505.jar/ was not resolved.
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2013-10-18 14:43:13.220
!MESSAGE Missing required bundle org.eclipse.core.jobs_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2013-10-18 14:43:13.220
!MESSAGE Missing required bundle org.eclipse.core.contenttype_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2013-10-18 14:43:13.220
!MESSAGE Missing required bundle org.eclipse.equinox.preferences_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2013-10-18 14:43:13.220
!MESSAGE Missing required bundle org.eclipse.equinox.registry_[3.4.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2013-10-18 14:43:13.220
!MESSAGE Missing required bundle org.eclipse.equinox.app_[1.0.0,2.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-10-18 14:43:13.220
!MESSAGE Bundle initial@reference:file:plugins/org.eclipse.equinox.ds_1.2.1.R36x_v20100803.jar/ was not resolved.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.220
!MESSAGE Missing imported package org.osgi.service.component_1.1.0.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.221
!MESSAGE Missing imported package org.eclipse.equinox.internal.util.threadpool_1.0.0.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.221
!MESSAGE Missing imported package org.osgi.service.log_1.3.0.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.221
!MESSAGE Missing imported package org.eclipse.equinox.internal.util.timer_1.0.0.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.221
!MESSAGE Missing imported package org.eclipse.equinox.internal.util.event_1.0.0.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.221
!MESSAGE Missing imported package org.eclipse.equinox.internal.util.hash_1.0.0.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.221
!MESSAGE Missing imported package org.osgi.service.metatype_1.1.0.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.221
!MESSAGE Missing imported package org.eclipse.equinox.internal.util.pool_1.0.0.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.221
!MESSAGE Missing imported package org.osgi.service.cm_1.2.0.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.221
!MESSAGE Missing imported package org.eclipse.equinox.internal.util.ref_1.0.0.

!ENTRY org.eclipse.osgi 2 0 2013-10-18 14:43:13.234
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-10-18 14:43:13.234
!MESSAGE Bundle org.eclipse.core.runtime_3.6.0.v20100505 [2] was not resolved.
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2013-10-18 14:43:13.234
!MESSAGE Missing required bundle org.eclipse.core.jobs_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2013-10-18 14:43:13.234
!MESSAGE Missing required bundle org.eclipse.equinox.registry_[3.4.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2013-10-18 14:43:13.234
!MESSAGE Missing required bundle org.eclipse.equinox.preferences_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2013-10-18 14:43:13.234
!MESSAGE Missing required bundle org.eclipse.core.contenttype_[3.3.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2013-10-18 14:43:13.234
!MESSAGE Missing optionally required bundle org.eclipse.core.runtime.compatibility.auth_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2013-10-18 14:43:13.234
!MESSAGE Missing required bundle org.eclipse.equinox.app_[1.0.0,2.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2013-10-18 14:43:13.235
!MESSAGE Missing dynamically imported package org.eclipse.core.internal.runtime.auth_0.0.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2013-10-18 14:43:13.235
!MESSAGE Bundle org.eclipse.equinox.ds_1.2.1.R36x_v20100803 [3] was not resolved.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.235
!MESSAGE Missing imported package org.eclipse.equinox.internal.util.event_1.0.0.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.235
!MESSAGE Missing imported package org.eclipse.equinox.internal.util.hash_1.0.0.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.235
!MESSAGE Missing imported package org.eclipse.equinox.internal.util.pool_1.0.0.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.235
!MESSAGE Missing imported package org.eclipse.equinox.internal.util.ref_1.0.0.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.235
!MESSAGE Missing imported package org.eclipse.equinox.internal.util.threadpool_1.0.0.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.235
!MESSAGE Missing imported package org.eclipse.equinox.internal.util.timer_1.0.0.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.235
!MESSAGE Missing imported package org.osgi.service.cm_1.2.0.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.235
!MESSAGE Missing imported package org.osgi.service.component_1.1.0.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.235
!MESSAGE Missing imported package org.osgi.service.log_1.3.0.
!SUBENTRY 2 org.eclipse.equinox.ds 2 0 2013-10-18 14:43:13.235
!MESSAGE Missing imported package org.osgi.service.metatype_1.1.0.

!ENTRY org.eclipse.osgi 4 0 2013-10-18 14:43:13.236
!MESSAGE Application error
!STACK 1
java.lang.IllegalStateException: Unable to acquire application service. Ensure that the org.eclipse.core.runtime bundle is resolved and started (see config.ini).
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:74)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:369)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:60)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:37)
	at java.lang.reflect.Method.invoke(Method.java:611)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:620)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:575)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1408)
	at org.eclipse.equinox.launcher.Main.main(Main.java:1384)
```

Config.ini:
```
# Product Runtime Configuration File

osgi.splashPath=platform:/base/plugins/ilog.odms.ide.rcp

eclipse.application=ilog.odms.ide.rcp.application
eclipse.product=ilog.odms.ide.rcp.product

osgi.bundles=\
    org.eclipse.equinox.common@2:start,\
    org.eclipse.update.configurator@3:start,\
    org.eclipse.core.runtime@start,\
    org.eclipse.equinox.common@2:start,\
    org.eclipse.equinox.ds@2:start,\
    org.eclipse.equinox.simpleconfigurator@1:start
osgi.bundles.defaultStartLevel=4
osgi.bundlefile.limit=100

#eclipse.p2.data.area=
#eclipse.p2.profile=SDKProfile

osgi.instance.area=@user.home/Application Data/IBM/ILOG/CPLEX_Studio125/workspace

eclipse.buildId=Build 0
```

---

