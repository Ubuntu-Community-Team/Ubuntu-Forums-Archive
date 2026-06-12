---
title: "foundationstone java app"
date: 2005-08-09
forum: General Help
---

### Post by liraz on 2005-08-09
I'm trying to get a hebrew teaching application working in linux, so far unsuccesfully.

For those interested it is located at - [http://foundationstone.com.au/HtmlSupport/FrameSupport/registerCGIFrame.html](http://foundationstone.com.au/HtmlSupport/FrameSupport/registerCGIFrame.html)


When running the shell script within the Foundationstone directory I get the following:
> 
yonatan@yonatan-9njaoje:~/FoundationStone_2.3$ Exception in thread "main" java.lang.UnsatisfiedLinkError: init
        at sun.awt.motif.MToolkit.init(Native Method)
        at sun.awt.motif.MToolkit.<init>(Unknown Source)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
        at java.lang.reflect.Constructor.newInstance(Unknown Source)
        at java.lang.Class.newInstance0(Unknown Source)
        at java.lang.Class.newInstance(Unknown Source)
        at java.awt.Toolkit$2.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Unknown Source)
        at javax.swing.UIManager.initialize(Unknown Source)
        at javax.swing.UIManager.maybeInitialize(Unknown Source)
        at javax.swing.UIManager.getUI(Unknown Source)
        at javax.swing.JButton.updateUI(Unknown Source)
        at javax.swing.AbstractButton.init(Unknown Source)
        at javax.swing.JButton.<init>(Unknown Source)
        at javax.swing.JButton.<init>(Unknown Source)
        at au.com.foundationstone.ui.UIUtilities.<clinit>(UIUtilities.java:44)
        at au.com.foundationstone.ui.FSLauncher.main(FSLauncher.java:13)

I have 0 idea how to decipher this. After long time googling and searching I am still lost. There is a very old debian guide for installing the application located here:
[http://foundationstone.com.au/HtmlSupport/OnlineHelp/TroubleShootin]("http://foundationstone.com.au/HtmlSupport/OnlineHelp/TroubleShooting/DebianUnixHowTo.html")[g/DebianUnixHowTo.html]("http://foundationstone.com.au/HtmlSupport/OnlineHelp/TroubleShooting/DebianUnixHowTo.html")

It is for an old version of the program with many commands not working. Apparently I am supposed to install the fonts for this program to work, but the commands in the guide do not work. I have tried copying the fonts (.ps renamed to .pfa) to fonts:// but get greeted with "error: unsupported operation".

If anyone can help me with this, java related problem...please! :/

---

