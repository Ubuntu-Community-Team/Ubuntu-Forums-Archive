---
title: "What to use to open programs/software, etc ?"
date: 2008-06-20
forum: General Help
---

### Post by no2guncntrl on 2008-06-20
I've tried to figure this out myself but am not getting anywhere.
When I used to download programs or software in Windows off the net,
I would save to  file and then after the download would finish I would just
click "run" and the program or software would open. 

Now I'm trying to use Ubuntu instead of Windows but am having probs
trying to find an app or anything for that matter that will open downloaded
programs or software. I installed Zipper for zip files, but I can't anything
to open up. I downloaded Avira for Linux and it comes up with a tar.gz.
Here's the file from here. >

[http://free-av.com/en/download/download_servers.php](http://free-av.com/en/download/download_servers.php)
Md5: e333fe7abd990128316bf46c43c72222

What the heck is that and how do I get this to open ? This isn't the only
program/software I haven't been able to open. What do I have to do
to get these different things to open. I'm lost, and I don't want to go back
to Windows if I can help it.

Thanks for any help or info. I appreciate it.
n2gc

---

### Post by Exsecrabilus on 2008-06-20
> **no2guncntrl said:**
> I've tried to figure this out myself but am not getting anywhere.
When I used to download programs or software in Windows off the net,
I would save to  file and then after the download would finish I would just
click "run" and the program or software would open. 

Now I'm trying to use Ubuntu instead of Windows but am having probs
trying to find an app or anything for that matter that will open downloaded
programs or software. I installed Zipper for zip files, but I can't anything
to open up. I downloaded Avira for Linux and it comes up with a tar.gz.
Here's the file from here. >

[http://free-av.com/en/download/download_servers.php](http://free-av.com/en/download/download_servers.php)
Md5: e333fe7abd990128316bf46c43c72222

What the heck is that and how do I get this to open ? This isn't the only
program/software I haven't been able to open. What do I have to do
to get these different things to open. I'm lost, and I don't want to go back
to Windows if I can help it.

Thanks for any help or info. I appreciate it.
n2gc
For handling .zip files, you want to run this in the Terminal:
```
sudo aptitude install unzip
```

For the Avira Antivirus, I would assume you do this:

Right-click the .tar.gz file and choose **Extract Here**.
Open up the newly-made folder and click the file called *install*.

---

### Post by sdennie on 2008-06-20
1) You probably don't need Avira.  It will probably only remove Windows viruses and, unless you are running a mail server, it's probably not needed.

2) The easiest way for newcomers to install software on Ubuntu is to go to Applications->Add/Remove.  You will rarely, if ever, need to actually use a web browser to download software with Ubuntu.  (Make sure "Show: " is set to All Available Applications in the Add/Remove application).

---

### Post by no2guncntrl on 2008-06-20
Thank you for the help. I'm still confused regarding how to go about this,
but I'll take time and read some of the tips and sticky's. Sooner or later
I'll get it.

---

### Post by sdennie on 2008-06-20
> **no2guncntrl said:**
> Thank you for the help. I'm still confused regarding how to go about this,
but I'll take time and read some of the tips and sticky's. Sooner or later
I'll get it.

If you are coming from Windows, it's a big shift in how getting software works.  There are many thousands of open source applications that are literally a click away using Applications->Add/Remove or System->Administration->Synaptic Package Manager.  Once you get used to the fact that nearly any piece of software you could possible want is available, open source and simple to install, you'll appreciate the system a lot more.  :)

---

### Post by no2guncntrl on 2008-06-20
^^ Thank you. I just now took a closer look at the Synaptic Mgr and like the
looks of that.  I can see already that will help me a lot. I'll read the help
files and get things going.

Appreciate the leads, gents.
n2gc.

---

