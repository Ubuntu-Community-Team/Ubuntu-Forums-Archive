---
title: "Rosetta Stone V3 / Wine No Workie!  Help?"
date: 2008-03-26
forum: General Help
---

### Post by Ubun00btu on 2008-03-26
I've tried repeatedly to get Rosetta Stone language software installed via WINE.  I had some success with the previous version of WINE, but when I opened the program it would freeze at the first screen with the Rosetta Stone background with nothing on it.  After updating to the current version of WINE it won't even install at all, it quits the installation during the "copying files" phase of installation.

I'm running Gutsy 7.10, the most recent WINE and here's the terminal messages:

```


fixme:advapi:LookupAccountNameW (null) L"jeff" (nil) 0x34e974 (nil) 0x34e96c 0x34e970 - stub
fixme:advapi:LookupAccountNameW (null) L"jeff" 0x165e90 0x34e974 0x164840 0x34e96c 0x34e970 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values
err:ole:CoGetClassObject class {88d96a05-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d96a05-f192-11d4-a65f-0040963251e5} could be created for context 0x1
err:ole:CoGetClassObject class {88d969c0-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d969c0-f192-11d4-a65f-0040963251e5} could be created for context 0x1
fixme:msxml:DllCanUnloadNow 
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 2 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 4 ignored L"CreateFolder" table values
err:ole:CoGetClassObject class {88d96a05-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d96a05-f192-11d4-a65f-0040963251e5} could be created for context 0x1
err:ole:CoGetClassObject class {88d969c0-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d969c0-f192-11d4-a65f-0040963251e5} could be created for context 0x1
fixme:msxml:domdoc_createNode unhandled node type 2
fixme:msxml:DllCanUnloadNow 
err:msi:custom_get_thread_return Invalid Return Code -2302
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603

```

If there's something obvious that needs to be fixed, I apologize, I'm still pretty new at this.
Just point me in the right direction.

BTW I've already cleared and replaced the ~/.wine directory and run winecfg again.  No success.  I've also tried it directly from the CD, as well as making an ISO, always navigating to "Setup.exe" via WINE either in GUI or Terminal.

---

### Post by mssever on 2008-03-27
Wine is mostly junk. You could file a regression bug on the wine website, and look there for any tips for running Rosetta Stone there.

Alternatively, you can check out l[ivemocha.com]("http://livemocha.com"), which has a similar concept.

---

### Post by CranKey on 2008-03-28
I'm also running 7.10 and the current version of wine, but I've had no problems with the install at all.  Mind you, I'm pretty sure I'm using a 2.x version of Rosetta Stone.

What I do have a problem with is that the program can't seem to find the language CD.  I'd like to mount an iso image of the CD and use that and while I was able to get it mounted and set the mount point in wine, it still couldn't find the data.  After that I tried with an actual CD but no joy there either.

As I said, the program installs and seems to run fine.  I think it would work if it could find the data files.

---

### Post by Ubun00btu on 2008-03-28
@mssever

I've checked the Wine site and haven't had much luck there, some folks are having trouble too, but the errors aren't the same.  I'll try submitting a bug report.  Thanks for the pointers to the other language site, it's worth using; but I actually own the Rosetta Stone CDs, so I'd like to get them to work...  I guess I'll just have to use them under XP if I can't.

@CranKey

Yeah, it's the newest Rosetta version, 3.0.  I don't have any of the older versions of the app; guess Wine hasn't caught up.

---

### Post by Kernel_Krunch on 2008-05-11
ok, to get a successful install of version 3.2 run this script 

[http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

I got it from [http://bugs.winehq.org/show_bug.cgi?id=12483](http://bugs.winehq.org/show_bug.cgi?id=12483) I don't know what the other person was saying about "no go" but it worked for me.

---

### Post by mcarlson on 2008-05-13
Bump.
I'm interested in seeing how to get this working.

If those who have it working can tell us how they have wine setup that might help.  XP or 2000, what do you have set to native rather than built in, etc.

A few hints from the code dump from Ubun00btu:
CoGetClassObject class {88d96a05-f192-11d4-a65f-0040963251e5}
This is from: XML DOM Document 6.0 Msxml2.DOMDocument.6.0

CoGetClassObject class {88d969c0-f192-11d4-a65f-0040963251e5}
This is from: XML DOM Document 4.0 Msxml2.DOMDocument.4.0

Looks like wine is having an XML problem with RS
For me I get past the install if I setup for 2K, but after it starts I get the RS background screen and nothing else happens.  When I run it under XP this is where it tells me there is an error so no speach recognition will work.  Then the program moves on and life is good.

---

### Post by Kernel_Krunch on 2008-05-14
> **mcarlson said:**
> Bump.
If those who have it working can tell us how they have wine setup that might help.  

Looks like wine is having an XML problem 

I just installed the wine package and ran the script I posted... like this

```
 sh winetricks msxml4 
```

the argument passed specifies xml... that should fix the problem like it did for me.

---

### Post by jack@tortuga on 2008-05-27
> 
I just installed the wine package and ran the script I posted... like this

```

 sh winetricks msxml4

```

the argument passed specifies xml... that should fix the problem like it did for me.



Awesome! I had the _exact_ same problem as the original poster, and this script worked like a charm!

---

### Post by pollodigomma on 2008-07-05
After successfully fetching the msxml4 installer, wine gives me a path error and aborts:

```
freddie@freddie-laptop:~$ sh winetricks msxml4
Warning: could not find DOS drive for current working directory '/home/freddie', starting in the Windows directory.
Warning: could not find DOS drive for current working directory '/home/freddie', starting in the Windows directory.
Cannot find cabextract.  Please install it (e.g. 'sudo apt-get install cabextract' or 'sudo yum install cabextract').
Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://download.microsoft.com/download/e/2/e/e2e92e52-210b-4774-8cd9-3a7a0130141d/msxml4-KB927978-enu.exe
--11:06:26--  http://download.microsoft.com/download/e/2/e/e2e92e52-210b-4774-8cd9-3a7a0130141d/msxml4-KB927978-enu.exe
           => `msxml4-KB927978-enu.exe'
Resolving download.microsoft.com... 209.84.1.126, 4.23.49.126, 209.84.1.124
Connecting to download.microsoft.com|209.84.1.126|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5,629,208 (5.4M) [application/octet-stream]

100%[====================================>] 5,629,208    334.89K/s    ETA 00:00

11:06:44 (310.70 KB/s) - `msxml4-KB927978-enu.exe' saved [5629208/5629208]

Warning: could not find DOS drive for current working directory '/home/freddie', starting in the Windows directory.
Executing wine /home/freddie/.winetrickscache/msxml4-KB927978-enu.exe /x:C:\winetrickstmp
Warning: could not find DOS drive for current working directory '/home/freddie', starting in the Windows directory.
wine: cannot find '/home/freddie/.winetrickscache/msxml4-KB927978-enu.exe'
Note: command 'wine /home/freddie/.winetrickscache/msxml4-KB927978-enu.exe /x:C:\winetrickstmp' returned status 2.  Aborting.
```

Any ideas why? The executable is right where the path indicates.

Edit: I managed it following the instructions found [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9742&iTestingId=17396") on AppDB.

---

