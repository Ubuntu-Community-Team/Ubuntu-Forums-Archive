---
title: "NX Windows Client won't connect"
date: 2005-10-12
forum: General Help
---

### Post by timw on 2005-10-12
Has anyone successfully connected to their NXServer running on Ubuntu from a windows box running the Nomachine NXClient?

I am having real problems with this.

I have searched on these forums and the web in general but have not found a problem similar to mine so any help will be great fully received.

I've installed "NXSERVER - Version 1.4.0-03 OS " with the nomachine key option (many times over!), added users and all that. Connected fine to my own ubuntu machine using the linux NXClient from mine and other people's linux boxes.

I then went to the Nomachine web site and downloaded their windows client ver 1.5.0-114. I created a config with my ubuntu username and password, specified my host ubuntu box by its IP address port 22. I try to connect and all that happens is the connection animation starts with the words "Setting up the x environment" and thats it. It does not error, or hang, it just sits there with this message until I give up on it and press the cancel button. I've checked the NXClient's log file but that it no help either:

> 
[Wed 12. Oct 10:55:33 2005]: Setting environment variable 'NX_SYSTEM' to 'C:\Program Files\NX Client for Windows'
[Wed 12. Oct 10:55:33 2005]: Setting environment variable 'NX_ROOT' to 'C:\Documents and Settings\MoinM\.nx'
[Wed 12. Oct 10:55:33 2005]: Setting environment variable 'NX_HOME' to 'C:\Documents and Settings\MoinM'
[Wed 12. Oct 10:55:34 2005]: Starting NX Client version 1.5.0-114
[Wed 12. Oct 10:55:34 2005]: Starting font debug
Setting font from nxclient.conf: 'MS Shell Dlg,8.3,-1,5,50,0,0,0,0,0'
Font was set to: 'MS Shell Dlg'
And the result is: 'MS Shell Dlg'
End of font debug


[Wed 12. Oct 10:55:34 2005]: Initializing the login dialog.
[Wed 12. Oct 10:55:34 2005]: Config File Name set to: 'C:/Documents and Settings/MoinM/.nx/config/nxclient.conf'.
[Wed 12. Oct 10:55:34 2005]: System NX dir set to: 'C:\Program Files\NX Client for Windows'.
[Wed 12. Oct 10:55:34 2005]: Personal NX dir set to: 'C:\Documents and Settings\MoinM\.nx'.
[Wed 12. Oct 10:55:34 2005]: creating SessionSettings=''
[Wed 12. Oct 10:55:34 2005]: LoginDialog::loadConfigFiles - number of entires in config dir: 4
[Wed 12. Oct 10:55:34 2005]: load 'tim' while sessionName=''
[Wed 12. Oct 10:55:34 2005]: LoginDialog: slotChangeSession [tim]
[Wed 12. Oct 10:55:34 2005]: LoginDialog: loadUserAndPassword
[Wed 12. Oct 10:55:34 2005]: load 'tim' while sessionName='tim'
[Wed 12. Oct 10:55:34 2005]: LoginDialog: slotChangeSession [tim]
[Wed 12. Oct 10:55:34 2005]: LoginDialog: loadUserAndPassword
[Wed 12. Oct 10:55:34 2005]: LoginDialog: loadUserAndPassword
[Wed 12. Oct 10:55:34 2005]: getShortName.b='C:\Program Files\NX Client for Windows'
[Wed 12. Oct 10:55:34 2005]: getShortName.a='C:\PROGRA~1\NXCLIE~1'
[Wed 12. Oct 10:55:34 2005]: Setting environment variable 'PATH' to 'C:\WINNT\system32;C:\WINNT;C:\WINNT\System32\Wbem;C:\Program Files\Microsoft SQL Server\80\Tools\BINN;C:\Program Files\Common Files\GTK\2.0\bin;C:\PROGRA~1\NXCLIE~1'
[Wed 12. Oct 10:55:34 2005]: Main: createTmpRegistryKey: cygwin temp directory found: [C:\Documents and Settings\MoinM\.nx\temp]
[Wed 12. Oct 10:55:35 2005]: WndSessionSettings: updateSambaStatus
[Wed 12. Oct 10:55:49 2005]: LoginDialog::loadConfigFiles - number of entires in config dir: 4
[Wed 12. Oct 10:55:49 2005]: load 'tim' while sessionName='tim'
[Wed 12. Oct 10:55:49 2005]: LoginDialog: slotChangeSession [tim]
[Wed 12. Oct 10:55:49 2005]: LoginDialog: loadUserAndPassword
[Wed 12. Oct 10:55:52 2005]: LoginDialog: closeEvent received!
[Wed 12. Oct 10:55:52 2005]: LoginDialog: stopAllTimers
[Wed 12. Oct 10:55:52 2005]: LoginDialog: stopProgressTimer


The line "[Wed 12. Oct 10:55:52 2005]: LoginDialog: closeEvent received!" is me pressing the cancel button (I know i didn't give it very long in this log file but I've left it for over an hour before with no difference).

I've successfully managed to putty to my ubuntu box from the windows box on port 22 so their is no network setup issued involved.

From reading around I've heard that "x" is a network protocol itself but with no error message being given I'm completely at a loss as to how to proceed.

Many thanks in advance!

Tim

---

