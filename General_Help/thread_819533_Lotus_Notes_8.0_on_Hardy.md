---
title: "Lotus Notes 8.0 on Hardy"
date: 2008-06-05
forum: General Help
---

### Post by kevn3k on 2008-06-05
Hi all, I've been following the installation for Lotus Notes 8.0 found here: [http://ubuntuforums.org/showthread.php?t=687679&highlight=lotus+notes](http://ubuntuforums.org/showthread.php?t=687679&highlight=lotus+notes) and I've hit a snag that doesn't seem to be affecting anyone else...

Everything goes smoothly, except it asks me to hit the wizard's next button twice

```
IBM Lotus Notes - InstallShield Wizard


Press 1 for Next, 2 for Previous, 3 to Cancel or 5 to Redisplay [1] 1

-------------------------------------------------------------------------------
IBM Lotus Notes - InstallShield Wizard


Press 1 for Next, 2 for Previous, 3 to Cancel or 5 to Redisplay [1] 1

-------------------------------------------------------------------------------
IBM Lotus Notes - InstallShield Wizard

Errors occurred during the installation.
  - Errors occurred during the installation.
- An error occurred and product installation failed. Look at the log file
/opt/IBM/Lotus/Notes/framework/rcp_install.log for details.

Press 3 to Finish or 5 to Redisplay [3]
```

and then the log file's output is this: 

```
(5-Jun-2008 12:35:13 PM), RCPCore-Install, com.ibm.pvc.install.wizard.CheckJVMAction, msg1, Set RCP_JVM_LOCATION = $N($N($P(absoluteInstallLocation)/framework,/)/rcp/eclipse/plugins/com.ibm.rcp.j2se.linux.x86_1.5.0.SR4-200707311521, /)
(5-Jun-2008 12:35:13 PM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set manifestSize = 502381
(5-Jun-2008 12:35:13 PM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set manifestDownloadSize = 238033
(5-Jun-2008 12:35:13 PM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_RESTART_PERSONALITY = 
(5-Jun-2008 12:35:13 PM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_INSTALL_FEATURES = RCP Platform Extension
Notes Platform Extension
Notes Plugin Integration
Notes Java Views and Search
Search
%Activities.name
Sametime
%Sametime.name
Sametime (core)
%Editors.name
%CAE.name
Feed Reader
(5-Jun-2008 12:35:13 PM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_STATIC_PROVISIONING = true
(5-Jun-2008 12:35:13 PM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_PROVISIONING_RETURN_CODE = 0
(5-Jun-2008 12:35:13 PM), RCPCore-Install, com.ibm.wizard.platform.legacylinux.LegacyLinuxRegistryServiceImpl, dbg.registry, reading VPD from /root/vpd.properties
(5-Jun-2008 12:35:13 PM), RCPCore-Install, com.ibm.wizard.platform.legacylinux.LegacyLinuxRegistryServiceImpl, dbg.registry, reading VPD from /root/vpd.properties
(5-Jun-2008 12:35:37 PM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, target platform: displayName=;name=Linux;version=2.6.24-18-generic;arch=x86;parent=
(5-Jun-2008 12:35:37 PM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, condition platform: displayName=Linux Platform;name=Linux;version=.*;arch=.*;parent=
(5-Jun-2008 12:35:37 PM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, target platform: displayName=;name=Linux;version=2.6.24-18-generic;arch=x86;parent=
(5-Jun-2008 12:35:37 PM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, condition platform: displayName=Linux Platform;name=Linux;version=.*;arch=.*;parent=
(5-Jun-2008 12:35:37 PM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, target platform: displayName=;name=Linux;version=2.6.24-18-generic;arch=x86;parent=
(5-Jun-2008 12:35:37 PM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, condition platform: displayName=Windows (All);name=Windows .*;version=.*;arch=.*;parent=
(5-Jun-2008 12:35:37 PM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, target platform: displayName=;name=Linux;version=2.6.24-18-generic;arch=x86;parent=
(5-Jun-2008 12:35:37 PM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, condition platform: displayName=Windows (All);name=Windows .*;version=.*;arch=.*;parent=
(5-Jun-2008 12:35:37 PM), RCPCore-Install, com.ibm.pvc.install.wizard.GenerateInstallIDAction, msg1, Set RCP_WORKSPACE_LOCATION = ${env.HOME}/Lotus/XPD
(5-Jun-2008 12:35:37 PM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_STATIC_PROVISIONING = false
(5-Jun-2008 12:35:37 PM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_PROVISIONING_RETURN_CODE = 8
(5-Jun-2008 12:35:37 PM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_PROVISIONING_STATUS = Manifest could not be found at this location: 
/root/install.xml
(5-Jun-2008 12:36:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Files (linuxJ2SEFiles): free=5267816 total=15686656
(5-Jun-2008 12:36:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Files (linuxJ2SEFiles)
(5-Jun-2008 12:36:12 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Files (linuxJ2SEFiles): free=4274104 total=15686656
(5-Jun-2008 12:36:12 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Uninstall Product Action (bean3): free=4169280 total=15686656
(5-Jun-2008 12:36:12 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Uninstall Product Action (bean3)
(5-Jun-2008 12:36:12 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Uninstall Product Action (bean3): free=4114488 total=15686656
(5-Jun-2008 12:36:12 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Files (commonCoreFiles): free=4060640 total=15686656
(5-Jun-2008 12:36:12 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Files (commonCoreFiles)
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Files (commonCoreFiles): free=270200 total=15686656
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Write Java Properties Action (createEclipseLinkFile): free=223496 total=15686656
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Write Java Properties Action (createEclipseLinkFile)
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Write Java Properties Action (createEclipseLinkFile): free=71312 total=15686656
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Write Java Properties Action (createRCPLinkFile): free=36592 total=15686656
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Write Java Properties Action (createRCPLinkFile)
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Write Java Properties Action (createRCPLinkFile): free=4768520 total=15686656
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Write Java Properties Action (createSharedLinkFile): free=4733904 total=15686656
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Write Java Properties Action (createSharedLinkFile)
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Write Java Properties Action (createSharedLinkFile): free=4621360 total=15686656
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Create Directory (deployDir): free=4576176 total=15686656
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Create Directory (deployDir)
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Create Directory (deployDir): free=4508288 total=15686656
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Generate Install Info Action (bean4): free=4407640 total=15686656
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Generate Install Info Action (bean4)
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Generate Install Info Action (bean4): free=4019512 total=15686656
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Write Java Properties Action (writeRCPLauncherProps): free=3974168 total=15686656
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Write Java Properties Action (writeRCPLauncherProps)
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Write Java Properties Action (writeRCPLauncherProps): free=3653504 total=15686656
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Uninstall Product Action (bean5): free=3588080 total=15686656
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Uninstall Product Action (bean5)
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Uninstall Product Action (bean5): free=3520104 total=15686656
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Files (group1RCPFiles): free=3470272 total=15686656
(5-Jun-2008 12:36:14 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Files (group1RCPFiles)
(5-Jun-2008 12:36:16 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Files (group1RCPFiles): free=5033664 total=15686656
(5-Jun-2008 12:36:16 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Uninstall Product Action (bean6): free=4998064 total=15686656
(5-Jun-2008 12:36:16 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Uninstall Product Action (bean6)
(5-Jun-2008 12:36:16 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Uninstall Product Action (bean6): free=4924664 total=15686656
(5-Jun-2008 12:36:16 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Files (group2CoreFiles): free=4792200 total=15686656
(5-Jun-2008 12:36:16 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Files (group2CoreFiles)
(5-Jun-2008 12:36:18 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Files (group2CoreFiles): free=3194896 total=16735232
(5-Jun-2008 12:36:18 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Uninstall Product Action (bean7): free=3133264 total=16735232
(5-Jun-2008 12:36:18 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Uninstall Product Action (bean7)
(5-Jun-2008 12:36:18 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Uninstall Product Action (bean7): free=3063888 total=16735232
(5-Jun-2008 12:36:18 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Files (group3CoreFiles): free=3024712 total=16735232
(5-Jun-2008 12:36:18 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Files (group3CoreFiles)
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Files (group3CoreFiles): free=3978784 total=16735232
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Uninstall Product Action (bean8): free=3893712 total=16735232
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Uninstall Product Action (bean8)
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Uninstall Product Action (bean8): free=3837992 total=16735232
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Files (linuxCoreFiles): free=3806224 total=16735232
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Files (linuxCoreFiles)
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Files (linuxCoreFiles): free=5397024 total=16735232
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Process Keystore Action (processKeystore): free=5310992 total=16735232
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Process Keystore Action (processKeystore)
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.pvc.install.product.ProcessKeystoreAction, dbg, copying /home/kevan/Lotus/deploy/.keystore.JCEKS.IBM_J9_VM.install to /opt/IBM/Lotus/Notes/framework/rcp/deploy
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Process Keystore Action (processKeystore): free=5148952 total=16735232
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Copy File To From Plugin Action (copyPluginCustomizationFromPlatform): free=5064984 total=16735232
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Copy File To From Plugin Action (copyPluginCustomizationFromPlatform)
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.pvc.install.product.CopyFileToFromPluginAction, msg1, RETURNING  /opt/IBM/Lotus/Notes/framework/rcp/eclipse/plugins/com.ibm.rcp.base_6.1.1.200707311521
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Copy File To From Plugin Action (copyPluginCustomizationFromPlatform): free=4882256 total=16735232
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Merge INI Action (mergePluginCustomization): free=4783936 total=16735232
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Merge INI Action (mergePluginCustomization)
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Merge INI Action (mergePluginCustomization): free=4683568 total=16735232
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Delete File (deletePlatformPluginCustomization): free=4589360 total=16735232
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Delete File (deletePlatformPluginCustomization)
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Delete File (deletePlatformPluginCustomization): free=4589216 total=16735232
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Write Java Properties Action (updateVMInRCPLauncherProps): free=4492960 total=16735232
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Write Java Properties Action (updateVMInRCPLauncherProps)
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Write Java Properties Action (updateVMInRCPLauncherProps): free=4277904 total=16735232
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Process Install Manifest Action (processInstallManifest): free=4277904 total=16735232
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Process Install Manifest Action (processInstallManifest)
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.pvc.install.product.ProcessInstallManifestAction, err, An error occurred and product installation failed.  Look at the log file /opt/IBM/Lotus/Notes/framework/rcp_install.log for details.
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.pvc.install.product.ProcessInstallManifestAction, err, ProductException: (error code = 601; message="err"; additional data = [/root/install.xml (No such file or directory)])
STACK_TRACE: 26
ProductException: (error code = 601; message="err"; additional data = [/root/install.xml (No such file or directory)])
	at com.ibm.pvc.install.ProductUtil.failInstall(ProductUtil.java:43)
	at com.ibm.pvc.install.ProductUtil.failAction(ProductUtil.java:51)
	at com.ibm.pvc.install.product.ProcessInstallManifestAction.processManifest(ProcessInstallManifestAction.java:126)
	at com.ibm.pvc.install.product.ProcessInstallManifestAction.install(ProcessInstallManifestAction.java:53)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.installProductAction(PureJavaProductServiceImpl.java:2969)
	at com.ibm.wizard.platform.linux.LinuxProductServiceImpl.installProductAction(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallProduct.getResultForProductAction(PureJavaProductServiceImpl.java:8048)
	at com.installshield.product.service.product.InstallableObjectVisitor.visitComponent(Unknown Source)
	at com.installshield.product.service.product.InstallableObjectVisitor.visitInstallableComponents(Unknown Source)
	at com.installshield.product.service.product.InstallableObjectVisitor.visitProductBeans(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallProduct.install(PureJavaProductServiceImpl.java:7199)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.installProduct(PureJavaProductServiceImpl.java:2637)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:64)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:615)
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.product.GenericProductService.installProduct(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.installAssembly(PureJavaProductServiceImpl.java:5523)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.access$900(PureJavaProductServiceImpl.java:119)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$Installer.execute(PureJavaProductServiceImpl.java:5378)
	at com.installshield.wizard.service.AsynchronousOperation.run(Unknown Source)
	at java.lang.Thread.run(Thread.java:803)

(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, uninstalling Write Java Properties Action (updateVMInRCPLauncherProps)
(5-Jun-2008 12:36:20 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, uninstalling Process Install Manifest Action (processInstallManifest)
(5-Jun-2008 1:04:04 PM), RCPCore-Install, com.ibm.pvc.install.wizard.CheckJVMAction, msg1, Set RCP_JVM_LOCATION = $N($N($P(absoluteInstallLocation)/framework,/)/rcp/eclipse/plugins/com.ibm.rcp.j2se.linux.x86_1.5.0.SR4-200707311521, /)
(5-Jun-2008 1:04:04 PM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set manifestSize = 502381
(5-Jun-2008 1:04:04 PM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set manifestDownloadSize = 238033
(5-Jun-2008 1:04:04 PM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_RESTART_PERSONALITY = 
(5-Jun-2008 1:04:04 PM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_INSTALL_FEATURES = RCP Platform Extension
Notes Platform Extension
Notes Plugin Integration
Notes Java Views and Search
Search
%Activities.name
Sametime
%Sametime.name
Sametime (core)
%Editors.name
%CAE.name
Feed Reader
(5-Jun-2008 1:04:04 PM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_STATIC_PROVISIONING = true
(5-Jun-2008 1:04:04 PM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_PROVISIONING_RETURN_CODE = 0
(5-Jun-2008 1:04:04 PM), RCPCore-Install, com.ibm.wizard.platform.legacylinux.LegacyLinuxRegistryServiceImpl, dbg.registry, reading VPD from /root/vpd.properties
(5-Jun-2008 1:04:04 PM), RCPCore-Install, com.ibm.wizard.platform.legacylinux.LegacyLinuxRegistryServiceImpl, dbg.registry, reading VPD from /root/vpd.properties
(5-Jun-2008 1:04:32 PM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, target platform: displayName=;name=Linux;version=2.6.24-18-generic;arch=x86;parent=
(5-Jun-2008 1:04:32 PM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, condition platform: displayName=Linux Platform;name=Linux;version=.*;arch=.*;parent=
(5-Jun-2008 1:04:32 PM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, target platform: displayName=;name=Linux;version=2.6.24-18-generic;arch=x86;parent=
(5-Jun-2008 1:04:32 PM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, condition platform: displayName=Linux Platform;name=Linux;version=.*;arch=.*;parent=
(5-Jun-2008 1:04:32 PM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, target platform: displayName=;name=Linux;version=2.6.24-18-generic;arch=x86;parent=
(5-Jun-2008 1:04:32 PM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, condition platform: displayName=Windows (All);name=Windows .*;version=.*;arch=.*;parent=
(5-Jun-2008 1:04:32 PM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, target platform: displayName=;name=Linux;version=2.6.24-18-generic;arch=x86;parent=
(5-Jun-2008 1:04:32 PM), RCPCore-Install, com.installshield.product.conditions.PlatformProductBeanCondition, dbg.platform, condition platform: displayName=Windows (All);name=Windows .*;version=.*;arch=.*;parent=
(5-Jun-2008 1:04:32 PM), RCPCore-Install, com.ibm.pvc.install.wizard.GenerateInstallIDAction, msg1, Set RCP_WORKSPACE_LOCATION = ${env.HOME}/Lotus/XPD
(5-Jun-2008 1:04:32 PM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_STATIC_PROVISIONING = false
(5-Jun-2008 1:04:32 PM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_PROVISIONING_RETURN_CODE = 8
(5-Jun-2008 1:04:32 PM), RCPCore-Install, com.ibm.pvc.install.wizard.ReadInstallManifestAction, msg1, Set RCP_PROVISIONING_STATUS = Manifest could not be found at this location: 
/root/install.xml
(5-Jun-2008 1:05:08 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Files (linuxJ2SEFiles): free=8075568 total=18638848
(5-Jun-2008 1:05:08 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Files (linuxJ2SEFiles)
(5-Jun-2008 1:05:09 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Files (linuxJ2SEFiles): free=1540072 total=18638848
(5-Jun-2008 1:05:09 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Uninstall Product Action (bean3): free=1540072 total=18638848
(5-Jun-2008 1:05:09 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Uninstall Product Action (bean3)
(5-Jun-2008 1:05:09 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Uninstall Product Action (bean3): free=1409000 total=18638848
(5-Jun-2008 1:05:09 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Files (commonCoreFiles): free=1409000 total=18638848
(5-Jun-2008 1:05:09 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Files (commonCoreFiles)
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Files (commonCoreFiles): free=5450080 total=17707008
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Write Java Properties Action (createEclipseLinkFile): free=5450080 total=17707008
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Write Java Properties Action (createEclipseLinkFile)
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Write Java Properties Action (createEclipseLinkFile): free=5329176 total=17707008
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Write Java Properties Action (createRCPLinkFile): free=5329176 total=17707008
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Write Java Properties Action (createRCPLinkFile)
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Write Java Properties Action (createRCPLinkFile): free=5214488 total=17707008
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Write Java Properties Action (createSharedLinkFile): free=5097752 total=17707008
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Write Java Properties Action (createSharedLinkFile)
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Write Java Properties Action (createSharedLinkFile): free=4978968 total=17707008
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Create Directory (deployDir): free=4978968 total=17707008
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Create Directory (deployDir)
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Create Directory (deployDir): free=4978896 total=17707008
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Generate Install Info Action (bean4): free=4858064 total=17707008
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Generate Install Info Action (bean4)
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Generate Install Info Action (bean4): free=4179720 total=17707008
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Write Java Properties Action (writeRCPLauncherProps): free=4179720 total=17707008
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Write Java Properties Action (writeRCPLauncherProps)
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Write Java Properties Action (writeRCPLauncherProps): free=3786504 total=17707008
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Uninstall Product Action (bean5): free=3786504 total=17707008
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Uninstall Product Action (bean5)
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Uninstall Product Action (bean5): free=3655432 total=17707008
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Files (group1RCPFiles): free=3655432 total=17707008
(5-Jun-2008 1:05:11 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Files (group1RCPFiles)
(5-Jun-2008 1:05:13 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Files (group1RCPFiles): free=7114592 total=17707008
(5-Jun-2008 1:05:13 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Uninstall Product Action (bean6): free=7026248 total=17707008
(5-Jun-2008 1:05:13 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Uninstall Product Action (bean6)
(5-Jun-2008 1:05:13 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Uninstall Product Action (bean6): free=6952864 total=17707008
(5-Jun-2008 1:05:13 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Files (group2CoreFiles): free=6849072 total=17707008
(5-Jun-2008 1:05:13 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Files (group2CoreFiles)
(5-Jun-2008 1:05:15 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Files (group2CoreFiles): free=3915584 total=17707008
(5-Jun-2008 1:05:15 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Uninstall Product Action (bean7): free=3824096 total=17707008
(5-Jun-2008 1:05:15 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Uninstall Product Action (bean7)
(5-Jun-2008 1:05:15 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Uninstall Product Action (bean7): free=3769856 total=17707008
(5-Jun-2008 1:05:15 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Files (group3CoreFiles): free=3740768 total=17707008
(5-Jun-2008 1:05:15 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Files (group3CoreFiles)
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Files (group3CoreFiles): free=953104 total=16821760
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Uninstall Product Action (bean8): free=875344 total=16821760
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Uninstall Product Action (bean8)
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Uninstall Product Action (bean8): free=810880 total=16821760
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Files (linuxCoreFiles): free=761872 total=16821760
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Files (linuxCoreFiles)
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Files (linuxCoreFiles): free=5411824 total=16821760
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Process Keystore Action (processKeystore): free=5325792 total=16821760
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Process Keystore Action (processKeystore)
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.pvc.install.product.ProcessKeystoreAction, dbg, deleting /opt/IBM/Lotus/Notes/framework/rcp/deploy/.keystore.JCEKS.IBM_J9_VM.install from /opt/IBM/Lotus/Notes/framework/rcp/deploy
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.pvc.install.product.ProcessKeystoreAction, dbg, copying /home/kevan/Lotus/deploy/.keystore.JCEKS.IBM_J9_VM.install to /opt/IBM/Lotus/Notes/framework/rcp/deploy
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Process Keystore Action (processKeystore): free=5163464 total=16821760
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Copy File To From Plugin Action (copyPluginCustomizationFromPlatform): free=5079496 total=16821760
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Copy File To From Plugin Action (copyPluginCustomizationFromPlatform)
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.pvc.install.product.CopyFileToFromPluginAction, msg1, RETURNING  /opt/IBM/Lotus/Notes/framework/rcp/eclipse/plugins/com.ibm.rcp.base_6.1.1.200707311521
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Copy File To From Plugin Action (copyPluginCustomizationFromPlatform): free=4814792 total=16821760
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Merge INI Action (mergePluginCustomization): free=4814792 total=16821760
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Merge INI Action (mergePluginCustomization)
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Merge INI Action (mergePluginCustomization): free=4607928 total=16821760
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Delete File (deletePlatformPluginCustomization): free=4511672 total=16821760
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Delete File (deletePlatformPluginCustomization)
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Delete File (deletePlatformPluginCustomization): free=4511600 total=16821760
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Write Java Properties Action (updateVMInRCPLauncherProps): free=4413296 total=16821760
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Write Java Properties Action (updateVMInRCPLauncherProps)
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory after installing Write Java Properties Action (updateVMInRCPLauncherProps): free=4210544 total=16821760
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, dbg.install, JVM memory before installing Process Install Manifest Action (processInstallManifest): free=4210544 total=16821760
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, installing Process Install Manifest Action (processInstallManifest)
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.pvc.install.product.ProcessInstallManifestAction, err, An error occurred and product installation failed.  Look at the log file /opt/IBM/Lotus/Notes/framework/rcp_install.log for details.
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.pvc.install.product.ProcessInstallManifestAction, err, ProductException: (error code = 601; message="err"; additional data = [/root/install.xml (No such file or directory)])
STACK_TRACE: 26
ProductException: (error code = 601; message="err"; additional data = [/root/install.xml (No such file or directory)])
	at com.ibm.pvc.install.ProductUtil.failInstall(ProductUtil.java:43)
	at com.ibm.pvc.install.ProductUtil.failAction(ProductUtil.java:51)
	at com.ibm.pvc.install.product.ProcessInstallManifestAction.processManifest(ProcessInstallManifestAction.java:126)
	at com.ibm.pvc.install.product.ProcessInstallManifestAction.install(ProcessInstallManifestAction.java:53)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.installProductAction(PureJavaProductServiceImpl.java:2969)
	at com.ibm.wizard.platform.linux.LinuxProductServiceImpl.installProductAction(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallProduct.getResultForProductAction(PureJavaProductServiceImpl.java:8048)
	at com.installshield.product.service.product.InstallableObjectVisitor.visitComponent(Unknown Source)
	at com.installshield.product.service.product.InstallableObjectVisitor.visitInstallableComponents(Unknown Source)
	at com.installshield.product.service.product.InstallableObjectVisitor.visitProductBeans(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallProduct.install(PureJavaProductServiceImpl.java:7199)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.installProduct(PureJavaProductServiceImpl.java:2637)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:64)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:615)
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.product.service.product.GenericProductService.installProduct(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.installAssembly(PureJavaProductServiceImpl.java:5523)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.access$900(PureJavaProductServiceImpl.java:119)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$Installer.execute(PureJavaProductServiceImpl.java:5378)
	at com.installshield.wizard.service.AsynchronousOperation.run(Unknown Source)
	at java.lang.Thread.run(Thread.java:803)

(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, uninstalling Write Java Properties Action (updateVMInRCPLauncherProps)
(5-Jun-2008 1:05:17 PM), RCPCore-Install, com.ibm.wizard.platform.linux.LinuxProductServiceImpl, msg1, uninstalling Process Install Manifest Action (processInstallManifest)
```

Being new, I have *no* idea what all this means.  If anyone has any ideas as to what's gone wrong, I'd love to hear a solution :)  For some reason, I can't run my Lotus right from my Vista partition (it's a dual boot) through WINE (it just doesn't load... sometimes it will open the splash screen, but then just stops there).  Either a solution for Ubuntu or the WINE emulator would be fine, assuming the <name>.id file is still valid for the Linux version.

---

### Post by kevn3k on 2008-06-09
bump?

---

### Post by prshah on 2008-06-10
> **kevn3k said:**
> ```
ProductException: (error code = 601; message="err"; additional data = [/root/install.xml (No such file or directory)])
```

This probably means that the "deploy directory" is missing, from the installation location. > Change to the directory that contains the unpacked setup.sh installation executable.
 Note: Verify that the directory also contains the deploy directory, setup.sh, and updateSite.zip. These
 contain the needed **install manifest** and feature and plug-in JAR files.


---

### Post by hackmeister on 2008-06-11
Lotus Notes 8.5 beta 1 just came out. Ubuntu is now officially supported and they have a .deb package available:
[https://www14.software.ibm.com/webapp/iwm/web/preLogin.do?lang=en_US&source=swg-lnd85](https://www14.software.ibm.com/webapp/iwm/web/preLogin.do?lang=en_US&source=swg-lnd85)

---

### Post by gbrito on 2008-06-20
Hi, I install lotus Notes 8.0 over Hardy, without problem, follow the next link instructions....

[http://www-10.lotus.com/ldd/nd8forum.nsf/7756aedc25e6d81285256324005ac76c/f0d9785f39edce6a85257441000cfe42?OpenDocument](http://www-10.lotus.com/ldd/nd8forum.nsf/7756aedc25e6d81285256324005ac76c/f0d9785f39edce6a85257441000cfe42?OpenDocument)

Best regards...

GB...

---

