---
title: "TeamViewer: Your partner uses newer version of Teamviewer. Would you like to update.."
date: 2012-12-07
forum: General Help
---

### Post by Lyfang on 2012-12-07
Hi, I had some issues with the new TeamViewer deb v8.0.16485 beta. So I downloaded v7.0.9377 but then I got: "Your partner uses newer version of Teamviewer. Would you like to update Teamviewer now to establish connection?" So I installed version 8 again, which after a while worked fine and if not, I could kill Teamviewer and Wine (TeamViewer is running with Wine) with LXTask and restart TeamViewer. See also: [http://kaar3l.blogspot.se/2011/12/teamviewer-6-problem.html](http://kaar3l.blogspot.se/2011/12/teamviewer-6-problem.html) (The link talks about copying newer TeamViewer Windows files to the Linux system)

I will link to this thread from: [https://plus.google.com/101315094374188414722/posts/VQorrLLq1wZ](https://plus.google.com/101315094374188414722/posts/VQorrLLq1wZ)

---

### Post by haqking on 2012-12-07
> **Lyfang said:**
> Hi, I had some issues with the new TeamViewer deb v8.0.16485 beta. So I downloaded v7.0.9377 but then I got: "Your partner uses newer version of Teamviewer. Would you like to update Teamviewer now to establish connection?" So I installed version 8 again, which after a while worked fine and if not, I could kill Teamviewer and Wine (TeamViewer is running with Wine) with LXTask and restart TeamViewer. See also: [http://kaar3l.blogspot.se/2011/12/teamviewer-6-problem.html](http://kaar3l.blogspot.se/2011/12/teamviewer-6-problem.html) (The link talks about copying newer TeamViewer Windows files to the Linux system)

I will link to this thread from: [https://plus.google.com/101315094374188414722/posts/VQorrLLq1wZ](https://plus.google.com/101315094374188414722/posts/VQorrLLq1wZ)

I am confused, if you are using wine you would use the .exe not the .deb.  Why do you need wine ?

the version 8 beta works fine for me with no issues.

---

### Post by Lyfang on 2012-12-07
> **haqking said:**
> I am confused, if you are using wine you would use the .exe not the .deb.  Why do you need wine ?
No, I have not Wine installed. Use your file manager e.g. Nautilus and browse to */opt/teamviewer8/tv_bin/wine/bin* (you will see wine, wine-preloader and wineserver)
> **haqking said:**
> the version 8 beta works fine for me with no issues.
Sounds great! However I have some problems e.g.:
```
USERNAME@ubuntu:~$ teamviewer 

Init...
Checking setup...
Launching TeamViewer...
err:secur32:SECUR32_initSchannelSP libgnutls not found, SSL connections will fail
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32df64,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x32dc1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x32df64,0x00000000), stub!
```
I also posted at TeamViewer's Google+ page: *Please fix bugs before releasing the final product: [http://ubuntuforums.org/showthread.php?p=12392354&#65279;](http://ubuntuforums.org/showthread.php?p=12392354&#65279;)*

---

### Post by onedemian on 2012-12-11
I am having exactly the same problem. Ubuntu 12.04 LTS 64bits. It ran first time only, nore more after rebooting.

> **Lyfang said:**
> No, I have not Wine installed. Use your file manager e.g. Nautilus and browse to */opt/teamviewer8/tv_bin/wine/bin* (you will see wine, wine-preloader and wineserver)

Sounds great! However I have some problems e.g.:
```
USERNAME@ubuntu:~$ teamviewer 

Init...
Checking setup...
Launching TeamViewer...
err:secur32:SECUR32_initSchannelSP libgnutls not found, SSL connections will fail
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32df64,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x32dc1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x32df64,0x00000000), stub!
```
I also posted at TeamViewer's Google+ page: *Please fix bugs before releasing the final product: [http://ubuntuforums.org/showthread.php?p=12392354&#65279;](http://ubuntuforums.org/showthread.php?p=12392354&#65279;)*

---

### Post by onedemian on 2012-12-11
I am experiencing the same problem as described by Lyfang. Ubuntu 12.04 LTS 64 bits. It ran first time, but not after restarting. I restarted daemon, but same problem.

> **Lyfang said:**
> No, I have not Wine installed. Use your file manager e.g. Nautilus and browse to */opt/teamviewer8/tv_bin/wine/bin* (you will see wine, wine-preloader and wineserver)

Sounds great! However I have some problems e.g.:
```
USERNAME@ubuntu:~$ teamviewer 

Init...
Checking setup...
Launching TeamViewer...
err:secur32:SECUR32_initSchannelSP libgnutls not found, SSL connections will fail
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32df64,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x32dc1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x32df64,0x00000000), stub!
```
I also posted at TeamViewer's Google+ page: *Please fix bugs before releasing the final product: [http://ubuntuforums.org/showthread.php?p=12392354&#65279;](http://ubuntuforums.org/showthread.php?p=12392354&#65279;)*

---

### Post by sieg358 on 2012-12-12
> **onedemian said:**
> I am experiencing the same problem as described by Lyfang. Ubuntu 12.04 LTS 64 bits. It ran first time, but not after restarting. I restarted daemon, but same problem.

Same problem here as well, TV8 worked fine the first time and now after restarting I'm having the exact same issue. I then DLd TV7 and I get the message that my other machines are using the newer version.

---

### Post by Lyfang on 2012-12-13
> **sieg358 said:**
> Same problem here as well, TV8 worked fine the first time and now after restarting I'm having the exact same issue. I then DLd TV7 and I get the message that my other machines are using the newer version.
I think there should have been some backward compability. At least support for the previous version.

Also with TV8 libgnutls is not found but libgnutls26 GnuTLS is installed.

---

### Post by Lyfang on 2012-12-25
> **haqking said:**
> I am confused, if you are using wine you would use the .exe not the .deb.  Why do you need wine ?

the version 8 beta works fine for me with no issues.
  The Linux version of TV8 still more or less uses Wine. This custom version of Wine seems to work great. I hope TeamViewer will release the stable Linux version 8 soon. I could also try Wine and the Windows version of [TeamViewer Portable]("http://portableapps.com/apps/utilities/teamviewer_portable") 8.0.16642 latter, since Wine's uninstaller isn't well tested and is quite "shaky" at the moment.

---

