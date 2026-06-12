---
title: "Eclipse error on Ubuntu 6.10 especially"
date: 2007-01-06
forum: General Help
---

### Post by zenwalker on 2007-01-06
Hello friends,
I didnt find any suitable forum section to post this error. Please accept my apologies. 
Mods can move this thread to appropriate section but please make a note to me regarding this.

Comming on the problem:
I recently downloaded eclipse 3.2.1 package from its home page and installed sucessfully. But when ever i try to create a new Java project, its giving me error which says Java.lang.NullpointerException.

But when i tested the same package on other flavors (Zenwalk and Suse), its working fine. with same jdk package installed on these three flavors. So i concluded that its problem with ubuntu. So can any one tell me how to get rid of this??  

When i looked at error.log file of eclipse on ubuntu, these is the error i got:


!SESSION 2007-01-06 12:37:57.449 ----------------------------------------------- eclipse.buildId=M20060921-0945 java.fullversion=GNU libgcj 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7) BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_IN Command-line arguments: -os linux -ws gtk -arch x86 !ENTRY org.eclipse.jface 4 2 2007-01-06 12:40:58.607 !MESSAGE Problems occurred when invoking code from plug-in: "org.eclipse.jface". !STACK 0 java.lang.NullPointerException at org.eclipse.jdt.internal.ui.wizards.JavaProjectWizardFirstPage$JREGroup.getDefaultJVMName(JavaProjectWizardFirstPage.java:443) at org.eclipse.jdt.internal.ui.wizards.JavaProjectWizardFirstPage$JREGroup.getDefaultJVMLabel(JavaProjectWizardFirstPage.java:447) at org.eclipse.jdt.internal.ui.wizards.JavaProjectWizardFirstPage$JREGroup.<init>(JavaProjectWizardFirstPage.java:349) at org.eclipse.jdt.internal.ui.wizards.JavaProjectWizardFirstPage.createControl(JavaProjectWizardFirstPage.java:751) at org.eclipse.jface.wizard.Wizard.createPageControls(Wizard.java:180) at org.eclipse.jface.wizard.WizardDialog.createPageControls(WizardDialog.java:614) at org.eclipse.jface.wizard.WizardDialog.setWizard(WizardDialog.java:989) at org.eclipse.jface.wizard.WizardDialog.updateForPage(WizardDialog.java:1041) at org.eclipse.jface.wizard.WizardDialog.access$2(WizardDialog.java:1038) at org.eclipse.jface.wizard.WizardDialog$4.run(WizardDialog.java:1028) at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67) at org.eclipse.jface.wizard.WizardDialog.showPage(WizardDialog.java:1026) at org.eclipse.ui.internal.dialogs.NewWizardSelectionPage.advanceToNextPageOrFinish(NewWizardSelectionPage.java:71) at org.eclipse.ui.internal.dialogs.NewWizardNewPage$1.doubleClick(NewWizardNewPage.java:355) at org.eclipse.jface.viewers.StructuredViewer$1.run(StructuredViewer.java:796) at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37) at org.eclipse.core.runtime.Platform.run(Platform.java:843) at org.eclipse.ui.internal.JFaceUtil$1.run(JFaceUtil.java:44) at org.eclipse.jface.util.SafeRunnable.run(SafeRunnable.java:149) at org.eclipse.jface.viewers.StructuredViewer.fireDoubleClick(StructuredViewer.java:794) at org.eclipse.jface.viewers.AbstractTreeViewer.handleDoubleSelect(AbstractTreeViewer.java:1227) at org.eclipse.jface.viewers.StructuredViewer$4.widgetDefaultSelected(StructuredViewer.java:1158) at org.eclipse.jface.util.OpenStrategy.fireDefaultSelectionEvent(OpenStrategy.java:223) at org.eclipse.jface.util.OpenStrategy.access$0(OpenStrategy.java:220) at org.eclipse.jface.util.OpenStrategy$1.handleEvent(OpenStrategy.java:281) at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66) at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1085) at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3166) at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2842) at org.eclipse.jface.window.Window.runEventLoop(Window.java:820) at org.eclipse.jface.window.Window.open(Window.java:796) at org.eclipse.ui.actions.NewProjectAction.run(NewProjectAction.java:116) at org.eclipse.jface.action.Action.runWithEvent(Action.java:499) at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:539) at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:488) at org.eclipse.jface.action.ActionContributionItem$5.handleEvent(ActionContributionItem.java:400) at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66) at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1085) at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3166) at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2842) at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:1914) at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1878) at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:419) at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149) at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:95) at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78) at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92) at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68) at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400) at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177) at java.lang.reflect.Method.invoke(libgcj.so.70) at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336) at org.eclipse.core.launcher.Main.basicRun(Main.java:280) at org.eclipse.core.launcher.Main.run(Main.java:977) at org.eclipse.core.launcher.Main.main(Main.java:952) 

Can any body help me regarding this problem please?? Thanks atons.

---

### Post by ditsch on 2007-01-06
This appears to be a problem with the gcj-runtime. I do not assume you intend to use gcj but the SUN JRE. I suppose you did not run ```
sudo update-alternatives --config java
``` to select the SUN JRE, did you?

---

### Post by zenwalker on 2007-01-06
Nope, i dint do all those stuffs at all. All i manually did was extract the jdk package and put it in the /usr/java path and then setting its path in .bashrc file.

And for eclipse, its extracting package thats it. I didnt do any commands stuffs like what you said.

Thanks

---

### Post by zenwalker on 2007-01-06
Hello any help please??

---

### Post by ditsch on 2007-01-06
:confused:  Install Sun JDK, tell the system to use it (update-alternatives) and you're done. Nothing more.

---

### Post by zenwalker on 2007-01-06
> **ditsch said:**
> :confused:  Install Sun JDK, tell the system to use it (update-alternatives) and you're done. Nothing more.

I told you i have already installed 1.5 ver of JDK. So again as you have specified i have done here.

sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/bin/gij-wrapper-4.1). Nothing to configure.

So i am getting this. Now again when i checked on eclipse if its working, well unfortunately no. Its not working after doing this step.

Please help me. What to do next??

---

### Post by ditsch on 2007-01-06
Ahh, ok. So you did a manual extraction of the Sun JDK. But the system still does not know that you extracted JDK and where you extracted it. Extraction is only half-way to installation. You are still using gcj as default.

Now the question is: Why do you do such a complex thing, which software installation is, manually when there is such a wonderful method like ```
sudo aptitude sun-java5-jdk
``` All you have to do is to enable the multiverse repository.

Btw: Manually installing the JDK is best done with fakeroot to ensure the dependencies are fulfilled, necessary symlinks are created,... And the installation can be undone via apt.

---

### Post by Ramses de Norre on 2007-01-06
```
sudo aptitude install sun-java5-bin
```
will work better.
And you can also modify /etc/eclipse/java_home and set the location of JDK5 at the first line.
Then in eclipse select window > properties > java > installed jre's and make a new one pointing to jdk5 (the menu names can differ a little bit).

---

### Post by ditsch on 2007-01-06
Sorry, I always miss out the »install«. So, ```
sudo aptitude install sun-java5-jdk
``` The -bin package only installs the JRE which is sufficient to solve the problem. Anyway, to do Java development it is very helpful to have the JDK installed.

---

### Post by phossal on 2007-01-06
Here is my suggestion...

**[COLOR="#248"]1. Download Java[/COLOR]**
Download the [COLOR="Blue"][32Bit JDK]("http://java.sun.com/javase/downloads/index.jsp")[/COLOR] right from SUN.
You want this:* jdk-6-linux-i586.bin*

**[COLOR="#248"]2. Download Eclipse[/COLOR]**
Download the 32bit Eclipse right from [COLOR="Blue"][eclipse.org]("http://download.eclipse.org/eclipse/downloads/drops/R-3.2.1-200609210945/")[/COLOR]
You want this: *eclipse-SDK-3.2.1-linux-gtk.tar.gz *


**[COLOR="#248"]Installation[/COLOR]**
**A. **Eclipse simply needs to be extracted. 
**B.** The JDK requires that you run the install script. 
Rename the folder it produces to something simple: JDK6.32
**C.** Configure BASH to export the JAVA_HOME env variable like so: 


```

#BEG Copy and Paste
#Copy and Paste at the bottom of your /home/<user>/.bashrc file
#Then close all of your terminal windows. Reopen one, and type "eclipse"
# ~~~~~~~~~~~~~~~~~ JAVA (JDK,JRE) ~~~~~~~~~~~~~~~~~~~~~
export JAVA_HOME='/home/<user>/Desktop/JDK6.32'
PATH=.:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
#
# The eclipse alias below assumes that you have extracted the eclipse folder 
# to your desktop. It can be anywhere. Edit path as necessary
#
alias eclipse='java -jar /home/<user>/Desktop/eclipse/startup.jar'
#END Copy and Paste

```


**[COLOR="#248"]Additional Info[/COLOR]**
This is a very simple way to install the latest JDK. Obviously this method isn't supported by the package managers. You'll have to update on your own. The advantage is that the cooperation and performance of the two 32bit packages rivals the same on Windows. Also, this way, you can actually have multiple eclipses, JDK's, and, when you decide to, multiple Tomcat instances. They all can be installed in nearly the same way.


**[COLOR="#248"]Notes[/COLOR]**
Once eclipse is running, you'll need to change the default compiler, and possibly add the JRE:
Window -> Preferences -> Java -> Compiler (Set the version ie 6)
Window -> Preferences -> Java -> Installed JREs (Confirm your JRE)

A few times I've downloaded the JDK, only to be presented with an error that a file could not be found, and that installation could not continue. It seems that, occasionally, the file available for download has been prepared incorrectly. Once the problem is reported, and a few hours go by, I try again with success. It doesn't happen often, but it's happened more than once.

---

### Post by zenwalker on 2007-01-06
> **phossal said:**
> Here is my suggestion...

**[COLOR="#248"]1. Download Java[/COLOR]**
Download the [COLOR="Blue"][32Bit JDK]("http://java.sun.com/javase/downloads/index.jsp")[/COLOR] right from SUN.
You want this:* jdk-6-linux-i586.bin*

**[COLOR="#248"]2. Download Eclipse[/COLOR]**
Download the 32bit Eclipse right from [COLOR="Blue"][eclipse.org]("http://download.eclipse.org/eclipse/downloads/drops/R-3.2.1-200609210945/")[/COLOR]
You want this: *eclipse-SDK-3.2.1-linux-gtk.tar.gz *


**[COLOR="#248"]Installation[/COLOR]**
**A. **Eclipse simply needs to be extracted. 
**B.** The JDK requires that you run the install script. 
Rename the folder it produces to something simple: JDK6.32
**C.** Configure BASH to export the JAVA_HOME env variable like so: 


```

#BEG Copy and Paste
#Copy and Paste at the bottom of your /home/<user>/.bashrc file
#Then close all of your terminal windows. Reopen one, and type "eclipse"
# ~~~~~~~~~~~~~~~~~ JAVA (JDK,JRE) ~~~~~~~~~~~~~~~~~~~~~
export JAVA_HOME='/home/<user>/Desktop/JDK6.32'
PATH=.:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
#
# The eclipse alias below assumes that you have extracted the eclipse folder 
# to your desktop. It can be anywhere. Edit path as necessary
#
alias eclipse='java -jar /home/<user>/Desktop/eclipse/startup.jar'
#END Copy and Paste

```


**[COLOR="#248"]Additional Info[/COLOR]**
This is a very simple way to install the latest JDK. Obviously this method isn't supported by the package managers. You'll have to update on your own. The advantage is that the cooperation and performance of the two 32bit packages rivals the same on Windows. Also, this way, you can actually have multiple eclipses, JDK's, and, when you decide to, multiple Tomcat instances. They all can be installed in nearly the same way.


**[COLOR="#248"]Notes[/COLOR]**
Once eclipse is running, you'll need to change the default compiler, and possibly add the JRE:
Window -> Preferences -> Java -> Compiler (Set the version ie 6)
Window -> Preferences -> Java -> Installed JREs (Confirm your JRE)

A few times I've downloaded the JDK, only to be presented with an error that a file could not be found, and that installation could not continue. It seems that, occasionally, the file available for download has been prepared incorrectly. Once the problem is reported, and a few hours go by, I try again with success. It doesn't happen often, but it's happened more than once.


Hey thanks alot for all of you. That really solved the problem.

---

