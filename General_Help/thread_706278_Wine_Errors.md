---
title: "Wine Errors"
date: 2008-02-24
forum: General Help
---

### Post by RizingDamp on 2008-02-24
Hey Guys,

Well I just updated wine to the latest version wine-0.9.55 and I was just wondering about some of the terminal  output I am getting when running wine commands.  For example when I run wine notepad i get this in the terminal..... 
[B]
andrew@GamingRig:~$ wine notepad
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
[/B]

But notepad does open.


Also I dont have any entries for wine anymore in my drop down menus like I had before the update....wine help etc.

Is this normal with the new version?  Or has something gone wrong with the install?


Problem sorted..I reverted back to the older version

Thanks,

Andy.

---

### Post by ajgreeny on 2008-02-24
I've never used the terminal to open notepad before, in fact I don't actually use notepad at all, but just thought I'd try having seen your post.  I get exactly the same output in terminal and notepad opens OK, as yours did.  However, for all I know it may always have given this terminal output before, had I used it that way.

---

### Post by DJ_Peng on 2008-02-24
The menu listing issue is probably because rather than using Wine from the repos, if you got Wine from the source it probably uninstalled the changes Ubuntu made, including the menu items. I'm hoping they'll get an update to the repos soon so we can get the bugfixes in the latest Wine updates.

As far as the notepad issues go, I'm really surprised you're using the Windows Notepad rather than any of the Linux-based text editors. I understand it may be what you're used to, but even the default text editor is better than what I used in Windows. (Granted, I ditched Notepad for Notepad+ at least 3 or 4 years before I ditched Windows for Linux.)

---

### Post by DJ_Peng on 2008-02-24
You may also want to check the latest report from the [Wine Team]("https://wiki.ubuntu.com/TeamReports/February2008#head-d83a53c576d62e2ee899e2c629b9ee8e795707f3"). There's a known bug that may be helping cause what you're experiencing.

---

### Post by RizingDamp on 2008-02-25
Well I was only commenting about notepad and using the terminal becuase I read somewhere it was a way to test if wine was installed and working.  So I dont actually use notpad for text.  Im still very new to Linux having migrated from windows about 3 weeks ago and very much enjoying it so far, just scared to try to much in case I break something!!

With regards the wine menu items missing on the updated version, then yes I did get the updated version from the sources as I noticed the version in the repos was outdated.  

Well anyway Im finding my way slowly with alot of help from you guys.

So thank you very much for your responses.

Andy :)

---

### Post by DJ_Peng on 2008-02-25
Ah, ok. I hadn't heard of that being a good test case. Sorry about that. I usually just fire up winecfg to tweak the settings then dive in to one of the few things I need Windows for.

---

### Post by Nameless_one on 2008-02-25
I get that error too on all wine applications, but it doesn't seem to cause trouble. When running wine, expect to see a lot of console output that you won't understand. ;) What matters is wether the program runs correctly.

---

### Post by RizingDamp on 2008-02-26
Well now you guys have me thinking about something wine related.  Do you guys not use the terminal to install the windows .EXE, ie wine nameofprogram.exe.  With the new version of wine I get line after line of errors in the terminal when the EXE is installing.  I cant say if the installed windows application works because I have never completed the installation as I cancelled out part way through.  I was only trying it out to see if I understood the tutorials correctly.  Like I said earlier....Im just finding my way slowly.

Well once again thanks for all your feedback, Im finding these forums a fanatastic resource for us windows migrants and  Im sure even the Ubuntu experienced users. :)


Thanks,


Andy

---

### Post by DJ_Peng on 2008-02-26
I've only installed a few Windows apps, Dreamweaver and Firefox, plus CDVista, a CD cataloging program that doesn't quite play well with Wine (I need to try some more things), but usually I just drop in the CD and let the installer rock. In the case of CDVista I just doubled clicked on the installer. Linux is smart enough that it knows Wine needs to run the EXE files so when I do that Wine gets the handoff from Linux and does it's job. (The reason CDVista has issues is because it seems to require some database connectivity in Windows that I'm not willing to install yet, plus a version of IE, again something I'm not willing to install. I know there's a great program called IEs4Linux, but that ends me up with two installations of Wine (I think) and I don't want to waste the drive space for something I only need for a single app, especially since I've finally found a Linux native app that seems to handle most of the job.)

Back to your question, why are you canceling it out partway, and how far are you letting it get before killing it? Also, what particular app are you trying to install? One of us may have run across it before and have something for you to try with the particular app.

---

### Post by RizingDamp on 2008-02-26
DJ Peng,

I cancelled out the install because all I was trying to do was carry out parts of a wine tutorial.  I didn`t really want the windows software....like I said previously, I was just trying things out.


Once again many thanks for your help guys :)

---

### Post by DJ_Peng on 2008-02-26
Ah, gotcha.

---

