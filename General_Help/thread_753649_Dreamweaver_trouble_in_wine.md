---
title: "Dreamweaver trouble in wine"
date: 2008-04-12
forum: General Help
---

### Post by yoshimitsuspeed on 2008-04-12
When I try to launch dreamweaver it says 
err:module:attach_process_dlls "odbc32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Macromedia\\Dreamweaver 8\\dreamweaver.exe" failed, status c0000005

I copied the dll from system 32 in my windows sys and pasted it into sys and sys 32 in wine but it still comes up with the same error. WHat do I have to do to make it work?

---

### Post by warp99 on 2008-04-12
Are you using the latest version of wine from winehq.org?

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by yoshimitsuspeed on 2008-04-13
I am on hardy 8.x 64 bit.

I am running 0.9.59 from the repository.
I did have dreamweaver working on 64 bit gutsy from the repo version of wine. 
That installed with no trouble.

---

### Post by warp99 on 2008-04-13
That error is not specific to Dreamweaver since the odbc32.dll file could not be initialized and odbc32.dll is just a library for database export interpretation. Any programs that tried to access that library would get the same result, therefore this is a bug.

Now your best bet is to file a bug report over at winehq since the wine version in the Ubuntu repository is in universe and it's not maintained by Ubuntu. You can do that here:

[http://bugs.winehq.org/](http://bugs.winehq.org/)

---

### Post by yoshimitsuspeed on 2008-04-13
So since the file wasn't there to begin with doesn't make a difference?
I mean I don't have to manually make dreamweaver or wine aware that it's there now?

---

### Post by yoshimitsuspeed on 2008-04-13
Any thoughts?
I mean I don't want to go report a bug or contact winehq cause I am missing something stupid or something lol.

---

### Post by warp99 on 2008-04-14
> **yoshimitsuspeed said:**
> So since the file wasn't there to begin with doesn't make a difference?
I mean I don't have to manually make dreamweaver or wine aware that it's there now?

From the Wine Howto:
> An application may not work because Wine doesn't yet fully implement one of the DLL files the application is trying to use. If you encounter a DLL not found error, or see a lot of "FixMe:" messages while running the application in Wine, this is likely the case. **When this occurs, you can try using native (non-Wine) DLL files in place of Wine's builtin ones. Check the application database page for the program. There may be special configuration options or instructions for installing native DLL files there that you can try to get the application working. **For further configuration help, please see the Running Wine section of the User Guide.

**If the application still doesn't work, it's probably due to a bug or deficiency in Wine and we'd like to hear about it.** Please see the reporting bugs page for instructions on how to best report bugs with applications. Alternatively, if you're a programmer, we'd really like it if you tried to help us directly; please read the getting started with Wine development guide if you're interested.
[http://www.winehq.org/site/howto](http://www.winehq.org/site/howto)


There were no special instructions needed to install the .dll file, you placed the file in the  correct location, it did not work so you should fill out a bug report.

---

### Post by qbox on 2008-04-26
Same problem. I CAN'T solve it.

---

### Post by mpalencia on 2008-04-27
I´ve got the same problem, And it only happens in x86_64 either with .59 or .60, so far the only app that has this problem is dreamweaver, fireworks, flash work fine.

---

### Post by gilda on 2008-04-30
I managed to get past this on my box - 
By going into the wine config and overriding the odbc32 dll and then dropping the odbcint.dll in my wine system32 folder - the versions did not match but i was able to proceed and get dreamweaver to launch and work at that point

---

### Post by yoshimitsuspeed on 2008-04-30
Yeah I got it working too.
It was a while ago so I forget exactly what I did but I think it was about the same as glida. 
I think the first time I only added odbc32
I think it was when I added odbcint that it worked.

---

### Post by rzlatic on 2008-06-07
> **gilda said:**
> I managed to get past this on my box by going into the wine config and overriding the odbc32 dll

that's nice workaround for odbc32.dll.
it worked for me but as the wrestling with starting the dreamweaver.exe going on, now i'm stuck with ```
 Call from 0x6e22aca4 to unimplemented function msvcrt.dll._except_handler4_common, aborting
```

---

### Post by cogitordi on 2008-06-08
Using Heron/64 and Wine 1.0 RC4...

Trying to run TVAnts.

Same error as reported above:

~/.wine/drive_c/Program Files/TVAnts$ wine Tvants.exe 
err:module:attach_process_dlls "odbc32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\TVAnts\\Tvants.exe" failed, status c0000005

There's a bug for this:

[http://bugs.winehq.org/show_bug.cgi?id=13575](http://bugs.winehq.org/show_bug.cgi?id=13575)

---

### Post by cogitordi on 2008-06-14
> **gilda said:**
> going into the wine config and overriding the odbc32 dll and then dropping the odbcint.dll in my wine system32 folder

Thanks!

Just to be clear, after copying the Windows DLLs into the Wine System32 directory, set the override for ODBC32 to set "Native, then Built-In".

---

