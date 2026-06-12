---
title: "Need a little terminal help"
date: 2008-06-03
forum: General Help
---

### Post by C00P88 on 2008-06-03
Hi all, I know there are volumes of tutorials out there on how to use the terminal, but I don't have all day to pour over them. If I could get a little help I'd really appreciate it. I opened a bug for Quicken on bugzilla. I've been asked to provide the console output from the crash. I assume this means to try and run Quicken from the terminal and see what I get. Could someone look at what I've tried below and tell me what I'm doing wrong? I was told I need to do chdir before trying to run quicken, is this the same as cd? I can get Quicken to start up if I click the icon on the desktop, or through the Applications menu, but I'm having a heck of a time trying to run it from the terminal. (I'm running Ubuntu 8.04)

```
coop@Coops-PC:~$ wine quicken
wine: could not load L"C:\\windows\\system32\\quicken.exe": Module not found
coop@Coops-PC:~$ cd .wine
coop@Coops-PC:~/.wine$ quicken
bash: quicken: command not found
coop@Coops-PC:~/.wine$ cd wine
bash: cd: wine: No such file or directory
coop@Coops-PC:~/.wine$ cd quicken
bash: cd: quicken: No such file or directory
coop@Coops-PC:~/.wine$ cd .quicken
bash: cd: .quicken: No such file or directory
coop@Coops-PC:~/.wine$ ls
dosdevices  drive_c  system.reg  userdef.reg  user.reg
coop@Coops-PC:~/.wine$ cd drive_c
coop@Coops-PC:~/.wine/drive_c$ quicken
bash: quicken: command not found
coop@Coops-PC:~/.wine/drive_c$ ls
AnswerWorks 5.0  Program Files  windows
coop@Coops-PC:~/.wine/drive_c$ cd Program Files
bash: cd: Program: No such file or directory
coop@Coops-PC:~/.wine/drive_c$ cd AnserWorks 5.0
bash: cd: AnserWorks: No such file or directory
coop@Coops-PC:~/.wine/drive_c$ cd windows
coop@Coops-PC:~/.wine/drive_c/windows$ quicken
bash: quicken: command not found
coop@Coops-PC:~/.wine/drive_c/windows$ cd
coop@Coops-PC:~$ chdir wine quicken
bash: chdir: command not found
coop@Coops-PC:~$ 

```

---

### Post by bingoUV on 2008-06-03
I guess you need to do
```

cd ~/.wine/drive_c/windows/system32

```

---

### Post by Kinnza on 2008-06-03
they basicly told you to go to the lib where you installed this program and run it from there

you just didnt find it yet

im guessing its it 

cd ~/.wine/drive_c/program files/quicken

or something like that

---

### Post by FuturePilot on 2008-06-03
It will not be in System32. It will be in Program Files. But to cd to a directory with spaces in the name you need to use the escape character to escape the space. This character is \

So
```
cd ~/.wine/drive_c/Program\ Files/
```
I'm guessing it's in a directory called Quicken but I'm not sure. You can see all the directories with
```
ls
```

---

### Post by EXCiD3 on 2008-06-03
Yeah you need to cd to the directory where quicken is installed:

```
cd "~/.wine/drive_c/windows/Program Files/Quicken"
``` or whatever the actual directory is

then run quicken.exe with wine in terminal:

```
wine quicken.exe
```

And if you're not sure where quicken is located, just open Nautilus and show hidden folders and then browse to find the path easier. Like FuturePilot said, if there is a space in the folder name it requires a different syntax, or just use tab to finish typing the file/folder name for you.

---

### Post by C00P88 on 2008-06-03
Progress! I appreciate the help! I made it to the Program Files folder using the "\" symbol as suggested. Do I need to use sudo to run programs in the terminal? I've never been prompted for a password when I click the icons. Am I just using the wrong command to start qw.exe? I don't want to screw anything up. This is where I'm at:

```
coop@Coops-PC:~/.wine/drive_c$ cd Program\ Files
coop@Coops-PC:~/.wine/drive_c/Program Files$ Quicken
bash: Quicken: command not found
coop@Coops-PC:~/.wine/drive_c/Program Files$ cd Quicken
coop@Coops-PC:~/.wine/drive_c/Program Files/Quicken$ qw.exe
bash: qw.exe: command not found
coop@Coops-PC:~/.wine/drive_c/Program Files/Quicken$ qw
bash: qw: command not found
coop@Coops-PC:~/.wine/drive_c/Program Files/Quicken$ Quicken
bash: Quicken: command not found
coop@Coops-PC:~/.wine/drive_c/Program Files/Quicken$ quicken
bash: quicken: command not found
coop@Coops-PC:~/.wine/drive_c/Program Files/Quicken$ exec qw.exe
bash: exec: qw.exe: not found
coop@Coops-PC:~/.wine/drive_c/Program Files/Quicken$ init qw.exe
init: Need to be root
```

---

### Post by EXCiD3 on 2008-06-03
you need to do ```
wine qw.exe
```

---

### Post by wootah on 2008-06-03
> **C00P88 said:**
> Progress! I appreciate the help! I made it to the Program Files folder using the "\" symbol as suggested. Do I need to use sudo to run programs in the terminal? I've never been prompted for a password when I click the icons. Am I just using the wrong command to start qw.exe? I don't want to screw anything up. This is where I'm at:

```
coop@Coops-PC:~/.wine/drive_c$ cd Program\ Files
coop@Coops-PC:~/.wine/drive_c/Program Files$ Quicken
bash: Quicken: command not found
coop@Coops-PC:~/.wine/drive_c/Program Files$ cd Quicken
coop@Coops-PC:~/.wine/drive_c/Program Files/Quicken$ qw.exe
bash: qw.exe: command not found
coop@Coops-PC:~/.wine/drive_c/Program Files/Quicken$ qw
bash: qw: command not found
coop@Coops-PC:~/.wine/drive_c/Program Files/Quicken$ Quicken
bash: Quicken: command not found
coop@Coops-PC:~/.wine/drive_c/Program Files/Quicken$ quicken
bash: quicken: command not found
coop@Coops-PC:~/.wine/drive_c/Program Files/Quicken$ exec qw.exe
bash: exec: qw.exe: not found
coop@Coops-PC:~/.wine/drive_c/Program Files/Quicken$ init qw.exe
init: Need to be root
```

wine quicken.exe or wine Quicken.exe (whatever the case is, or qw.exe if that is what it is :))

---

### Post by aysiu on 2008-06-03
One you're in ~/.wine/drive_c/Program Files/Quicken, can you run the command ```
ls
``` and post the output?

If the command to run it is really *qw.exe*, you should be able to run it with ```
wine "z:\home\coop\.wine\drive_c\Program Files\Quicken\qw.exe"
```

---

### Post by C00P88 on 2008-06-03
Ok, output of ls below. I still have to type "wine quicken" even though I'm in the Quicken directory? One moment....

```

coop@Coops-PC:~/.wine/drive_c/Program Files/Quicken$ ls
alert.dll             lbt_Auto1Way.dll         Qsapi
alrtint8.dll          lbt_bullseye.dll         qsapi.dll
AnswerWorks           lbt_customerCentral.dll  qsapi_eng.dll
atwork.dll            lbt_decompression.dll    Qsetup.dll
atwork_xprint.dll     lbt.dll                  QShowHelp.dll
AWsetup2.log          lbt_excite.dll           qtax.dll
bagent.exe            lbtmngr.dll              quicken.ico
bgtbrwsr.dat          lbt_pvsync.dll           QuickenOLBackupLauncher.exe
bgt.dll               lbt_qplus.dll            QUpdate.bmp
bgt_pnf.dll           lbt_qupddir.dll          qvault.dll
billmind_alrtpkg.dll  lbt_rte.dll              qwapp.dll
billmind.exe          mmedia.ver               qwcntr.dll
billmind_qwrmnd.dll   mvbk14n.dll              qw.exe
BindContent.exe       mvcl14n.dll              qwinet.dll
bpbox.ocx             mvfs14n.dll              qwinver.dll
calnote.dll           mvix14n.dll              qwipa.dll
cashflow.dll          mvmc14n.dll              qwmain.dll
cashgen.dll           mvmg14n.dll              qwonline.dll
certs                 mvsr14n.dll              qwonlineFeatures.dll
cipher.dll            mvtl14n.dll              qwplan.dll
cnfirmfi.ini          mvut14n.dll              qwpr.dll
Convert03             ofxsdk_qw.dll            qwsnap.dll
convert_stub.dat      olbservice.dll           qwsync.dll
convert_stub.dll      online.dll               qwutil.dll
custprof.dll          onlncall.dll             QWVER.DLL
dbghelp.dll           patchw32.dll             qwwin.dll
decapi.dll            PDFDrv                   Release.txt
dedfindr.dat          phash.dat                RestartExe.exe
dellid.dll            pkgsettings.ini          SendError.dll
deluxe.ver            premier2008.ico          SendError.ini
dllapps_dbtred.dll    printenv.exe             Snap
dllapps_dedfnd.dll    qaccess.dll              Sounds
dllapps_ero.dll       qappid.ini               splash.png
dllapps_frcast.dll    qbillminder.gadget       sport.dll
dllapps_plan.dll      qcomutil.dll             TAX.PRI
dllapps_savgol.dll    qcon32.dll               TAX.SCD
ero.dat               QCONNECT.DLL             TAX.THP
err_rep.chm           QCustomAction.dll        techhelp.exe
fri.dat               qdapp.dll                ttaxexpt.dat
gdipapi.dll           qdappui.dll              ttaximp.dll
glbread.txt           qdb.dll                  txstuff.dll
graphs.dll            QHI.DAT                  UpdateContent.dll
helptl.dll            qhi.exe                  WhatsNew.pdf
ibill.dll             qif_ub.dat               xmlparse.dll
icconfig.ini          qindex.dll               xmlparse_tok.dll
imveng.dll            qnet.dll                 xport.dll
InetTools.dll         qrep.dll                 xsell.dll
Intellic.cat          qreports.dll
khash.dat             qsac.dll
coop@Coops-PC:~/.wine/drive_c/Program Files/Quicken$ 
```

---

### Post by C00P88 on 2008-06-03
I didn't see many .exe files from the ls command. This is what I got when I tried the qw.exe:

```
coop@Coops-PC:~/.wine/drive_c/Program Files/Quicken$ wine quicken
wine: could not load L"C:\\windows\\system32\\quicken.exe": Module not found
coop@Coops-PC:~/.wine/drive_c/Program Files/Quicken$ wine quicken.exe
wine: could not load L"C:\\windows\\system32\\quicken.exe": Module not found
coop@Coops-PC:~/.wine/drive_c/Program Files/Quicken$ wine qw.exe
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\Quicken\\QWUTIL.dll" failed with error 0
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\Quicken\\QWUTIL.tlb" failed with error 2
coop@Coops-PC:~/.wine/drive_c/Program Files/Quicken$ 
```

Would you agree the qw.exe is the correct file to run Quicken? When I go in through Nautilus and click the icon Quicken fires right up (but then crashes when I try to use it, hense the bug report ;)).

---

### Post by aysiu on 2008-06-03
Yes, you still have to type ```
wine qw.exe
``` even though you're in the Quicken directory. Wine is the actual program that runs .exe files.

---

### Post by EXCiD3 on 2008-06-03
Yes you have to type "wine qw.exe" to run it because you have to tell it you want Wine to run that executable. Its much different than windows. exe's aren't usable without wine in linux.

---

### Post by C00P88 on 2008-06-03
Ok, so I tried

```
wine "z:\home\coop\.wine\drive_c\Program Files\Quicken\qw.exe"
```

and still got 

```
coop@Coops-PC:~$ wine "z:\home\coop\.wine\drive_c\Program Files\Quicken\qw.exe"
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"Z:\\home\\coop\\.wine\\drive_c\\Program Files\\Quicken\\QWUTIL.dll" failed with error 0
err:ole:TLB_ReadTypeLib Loading of typelib L"Z:\\home\\coop\\.wine\\drive_c\\Program Files\\Quicken\\QWUTIL.tlb" failed with error 2
```

So I'm either really messing this up, or the above errors are what the guy from bugzilla wants? I thought the output would be longer?

---

### Post by EXCiD3 on 2008-06-03
Try opening the icon for Quicken in Text Editor and looking through it to see what line it executes to run Quicken. Then try that line in terminal.

I dont think thats the output that the guy wants because you said you actually were able to view the Quicken window by running it through the icon right? If this doesnt even get you that far, then its probably not the right error. It won't hurt to include it in your bug report though, the more information the better.

---

### Post by FuturePilot on 2008-06-03
> **C00P88 said:**
> Ok, so I tried

```
wine "z:\home\coop\.wine\drive_c\Program Files\Quicken\qw.exe"
```

and still got 

```
coop@Coops-PC:~$ wine "z:\home\coop\.wine\drive_c\Program Files\Quicken\qw.exe"
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"Z:\\home\\coop\\.wine\\drive_c\\Program Files\\Quicken\\QWUTIL.dll" failed with error 0
err:ole:TLB_ReadTypeLib Loading of typelib L"Z:\\home\\coop\\.wine\\drive_c\\Program Files\\Quicken\\QWUTIL.tlb" failed with error 2
```

So I'm either really messing this up, or the above errors are what the guy from bugzilla wants? I thought the output would be longer?

That looks to me like what they are asking for. Looks like a crash to me.

---

### Post by C00P88 on 2008-06-03
I right-clicked on the Quicken launcher in my panel and selected properties. Looks like qw.exe is the correct command.

env WINEPREFIX="/home/coop/.wine" wine "C:\Program Files\Quicken\qw.exe" 

Or is that different from opening the icon in gedit?

---

### Post by C00P88 on 2008-06-03
Ok thank you all very much for your help! I will submit the errors to bugzilla.

---

### Post by EXCiD3 on 2008-06-03
Should be the same thing. Gedit just gives you the raw text inside the file, the Properties page shows the text put into fields.

It looks to me like that error you get is the one you should post. Looks like the icon is running the same command as you did in terminal.

---

### Post by pschless on 2008-12-17
Having the same problem...

Ubuntu 8.10, Quicken 2009

---

