---
title: "[solved] Unable to start Abaqus on Focal Fossa"
date: 2021-07-02
forum: General Help
---

### Post by iutech on 2021-07-02
Hi all.
I'm trying to launch Abaqus 2020 on a Focal Fossa computer (not mine, one of my users, I'm the tech guy, I know nothing about FEM).
When launching it through ssh, I get this error :
```
No protocol specified
FXApp::openDisplay: unable to open display :0.0
Fatal Exception: connect
Abaqus Error: Abaqus/CAE Kernel exited with an error.
```

So I went in local and got this error instead :

```
X Error: code 2 major 151 minor 3: BadValue (integer parameter out of  range for operation).     
Warning: There was a problem creating an OpenGL feedback context for  printing.      
If you encounter any problems with printing, verify that indirect GLX  context   creation is enabled on your X server. For more information on indirect  / direct   GLX context and how to enable indirect GLX context creation, see  Knowledge Base   article QA00000043316     
 terminate called after throwing an instance of  'SMAAbuUtlConvertException'        
*** ABAQUS/ABQcaeG rank 0 terminated by signal 6 (Aborted)    ipc_CONNECTION_BROKEN    
Abaqus Error: Abaqus/CAE Kernel exited with an error.
```


I found someone having the exact same problem on [Arch]("https://bbs.archlinux.org/viewtopic.php?pid=1601017#p1601017") and using the *-mesa* switch I get rid of the OpenGL error but I still have the second part of the error : 

```
 terminate called after throwing an instance of       'SMAAbuUtlConvertException'                
*** ABAQUS/ABQcaeG rank 0 terminated by signal 6 (Aborted)                ipc_CONNECTION_BROKEN        
Abaqus Error: Abaqus/CAE Kernel exited with an error.
```

DuckDuckGo doesn't really find anything with this exact error, the closest I had was [there]("https://sourceforge.net/p/virtualgl/discussion/401860/thread/69e7db78/#3142") but the fix (adding os.environ = "1" to /installdir/6.x-x/site/abaqus_v6.env file) created a new error instead :
```
Traceback (most recent call last): 
  File "SMAPylModules/SMAPylDriverPy.m/src/driverEnv.py", line 347,  in envRunFile 
  File  "/usr/SIMULIA/EstProducts/2020/linux_a64/SMA/site/abaqus_v6.env",  line 31, in <module> 
    importEnv(driverUtils.getPlatform() + '.env') 
TypeError: string indices must be integers, not str 
Abaqus Error: Error when reading environment file  /usr/SIMULIA/EstProducts/2020/linux_a64/SMA/site/abaqus_v6.env 
```

So I just removed the os.environ="1" and was back to "terminate called after throwing an instance of       'SMAAbuUtlConvertException' "

Any idea on where this error comes from and how to solve it ?

---

### Post by iutech on 2021-07-07
The command* LANG=en_US.utf8 abaqus cae -mesa* was enough to solve the problem.

Apparently the problem came from the locale...

Now what's left is this error that appears in some situations : *Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 key *

Also, I installed the software without documentation, and now when I try to install the Documentation (Cloudview, Exalead) the installation stops on an error and I get this message : 
> The dependency check failed, please check logs.
Technical details:
Action LaunchAppAction from feature CODE\linux_a64\EXACloudView_inst failed.
Action ID: CheckDeps

Action LaunchMediaAction from feature CODE\linux_a64\AM_SIM_Abaqus_Extend.media failed.
Action ID: Launch_Media_EXALEAD_CloudView.Linux64_1.2


I did check the logs but they don't contain more information.

---

### Post by iutech on 2021-07-12
The error message (*The dependency check failed, please check logs.) *specifically appears at the phase "install EXALEAD Cloudview".
The problem is that installing the documentation leads to a screen asking for the path to the CloudView server, and refuses to pursue if none is provided.

---

### Post by iutech on 2022-04-26
From memory, it's not possible to install the Exalead cloudview (at least with the executable we have) and I didn't understand that it's possible to select not to install it but still install the documentation (which are step 2 and 3 of the installation process, the program itself being steps 4,5 and 6 IIRC).

So installing from step 1 fails, but installing from step 2 works.

---

