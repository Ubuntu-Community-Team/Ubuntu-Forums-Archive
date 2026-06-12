---
title: "Playonlinux vs Wine, also Wubi"
date: 2014-11-13
forum: General Help
---

### Post by robert137 on 2014-11-13
I am just now in the process of getting ready to try out Ubuntu; a long time Windows User and hate it!  

I see that there is some risk of repartitioning my c drive with windows and all apps  installed on it.  I can't afford to Bleep up my system and have to go through setting everything up again.  Is Wubi an intelligent choice to start to use Ubuntu?  Of course, that means Bleeping Windows is still running and sucking resources, when I'm running Ubuntu.  

However, maybe I need that, anyway, because while it's great that there is so much free software for Linux users, I need to be able to open existing docs, mind maps, etc.  I see that the Open Source Office App can open Word docs, but I've also seen notes that they may not look exactly the same, when opened.  So it look like for now, I do need access to Windows apps, because of existing files I am already working with.  

There is also something to be said about sticking with software you've already invested time in learning.  So then, yes, I need to be able to run Windows Apps in Ubuntu or else run them in Bleep Windows.  

've seen both Play On Linux and Vine mentioned as ways to run Windows apps on Ubuntu.  I wonder which is the best solution?  

For me, it seems that having access to Windows, for now is essential, so this installing into Windows may be the best choice, though some day, I'd like to set up a machine with only Ubuntu and Also be able to access docs already started in Windows.  I

f I'm running Ubuntu from within Windows, any suggestions on how to reduce resource sucking of Windows, when I am working with Ubuntu?  

I've covered multiple subjects; hope that's OK.  Feel free to paste my text and insert suggestions where appropriate.  

Thanks!

---

### Post by robert137 on 2014-11-13
If I already have Windows and a software installed on my machine and then install Ubuntu, using Wubi, how can I use Vine to run the software in Ubuntu?  Can I browse to a file within the already installed software?

My disk with all my software on it was hacked and is currently unavailable, so I don't have access to the original program file, just the installed software on my C drive.  Can this work, or will I need to run the software in Windows?

Thanks

---

### Post by Paulgirardin on 2014-11-13
Wubi is no longer maintained and is not recommended.It was only ever intended for short term trials.
You can set up Ubuntu in a VM within Windows or a better option is to create a dual boot system.Back up your important data.Make some room on your hard drive using the Windows disc utility to shrink the Windows partition.Burn a live DVD or a bootable thumb drive for Ubuntu.This will allow you to run a live session prior to installing Ubuntu,to determine if you like it and that your hard ware is compatible.Then,when you are ready, you can install Ubuntu as a dual boot,using the 'Something else" option in the installer,which will allow you to install the os to the space you made available.

---

### Post by Paulgirardin on 2014-11-13
Libre Office is very compatible with all Microsoft formats.I have never needed to use any other office suite.It is better to find Linux alternatives than trying to run Windows apps in Wine.There are many alternatives for most Windows software.

---

### Post by ibjsb4 on 2014-11-13
Play On Linux is a front end (GUI) for Wine.

[https://help.ubuntu.com/community/PlayOnLinux](https://help.ubuntu.com/community/PlayOnLinux)

Also click on the link below for a ton of ubuntu info.

---

### Post by robert137 on 2014-11-13
Hi,
Thanks for your reply.
I'd be very happy to leave Word behind, forever.  However, how would you deal with the following situation:
Let's say I've got some 100+ page books started in Word.  If I import them into Libre, a) will I lose formatting, etc that I've already done? b) because i.e. Kindle is set up to deal with Word docs, would I possibly be able to export it back to Word for uploading?  Or is that the kind of example, where I'd better stick with the software I started with?

I've also got Mind Maps in Mind Jet.  These are works in progress.  I don't know how to deal with this, other than to keep using Mind Jet, whatever that takes.  Yes, when I start new maps or docs, I will look for free apps to do them in, but for existing and there are many, then seems I'm stuck with the software that I've started them in.  What are your suggestions, given the above scenarios?  Thanks again!

---

### Post by Paulgirardin on 2014-11-13
I have no experience with those applications.Easiest option would be to install the windows version of Libre Office in windows and see if there are any formatting problems.
There are Linux alternatives to Mindjet,apparently. 
[http://mindjetalternatives.blogspot.co.nz/](http://mindjetalternatives.blogspot.co.nz/)

---

### Post by Impavidus on 2014-11-13
> **robert137 said:**
> I am just now in the process of getting ready to try out Ubuntu; a long time Windows User and hate it!  Ah, you hate Windows. Next question is, will you love Linux? That doesn't follow automatically.
> I see that there is some risk of repartitioning my c drive with windows and all apps  installed on it.  I can't afford to Bleep up my system and have to go through setting everything up again.  Is Wubi an intelligent choice to start to use Ubuntu?  Of course, that means Bleeping Windows is still running and sucking resources, when I'm running Ubuntu.As stated before, wubi is no longer supported (although it seems there are people who try to breath new life into it) and was never really meant for long term installs anyway. It always performs less than real dual boots. Installing as a real dual boot may be a little harder, but most beginners succeed. Some wipe their hard drive. Still, if you run Ubuntu via wubi, Windows is not running in the background and not sucking system resources other than hard drive space.
> However, maybe I need that, anyway, because while it's great that there is so much free software for Linux users, I need to be able to open existing docs, mind maps, etc.  I see that the Open Source Office App can open Word docs, but I've also seen notes that they may not look exactly the same, when opened.  So it look like for now, I do need access to Windows apps, because of existing files I am already working with.  

There is also something to be said about sticking with software you've already invested time in learning.  So then, yes, I need to be able to run Windows Apps in Ubuntu or else run them in Bleep Windows.You can start with making yourself familiar with the Linux software on Windows. Most open source software you get on Ubuntu, like LibreOffice, Gimp, Firefox, also has Windows versions. Once you are familiar with those applications and maybe have converted some old documents to native formats of those open source alternatives, changing to Ubuntu will be easier.

====Reading your next post from the preview page====

If you import your word doc into libreoffice, it's unlikely you'll lose all formatting. There may be errors in the more complicated things, like diagrams, placement of figures, tables. Text size, bold font, italics etc. should be fine. As many Windows users, you're the victim of vendor lock-in. MS wants you to stay with MS office, and therefore they make it difficult to use MS office format in different applications. Often best to use the simplest file format that does the job. I'm not familiar with kindles, but don't they support pdf format? If it's only for reading and no further editing is required, pdf is great as it is more or less guaranteed that the formatting will stay the same. You don't even get that when reading an MS Word2013 file on MS Word 2010 or whatever version numbers they actually used. Everything can convert to pdf.

---

### Post by robert137 on 2014-11-13
When I install as dual boot, can I jump back and forth between using Ubuntu and running a Windows software,  without rebooting?  If not, is there a practical way to set it up so I can do that.  That way I will use Ubuntu as much as possible, but when necessary, I could access Windows.  I guess the one downside is that that would likely require Windows to be running all the time and that sucks resources.  But maybe I could minimize what's running in Windows, so it would be little drag, but still give the convenience of having access to progs already installed.  What do you suggest?
Thanks!

---

### Post by nerdtron on 2014-11-13
1. I don't think wubi is still supported on the latest Ubuntu release?
2. You can run Ubuntu from a USB and then install wine but I don't think it will solve your problem. You can still browse drive C: on Ubuntu and you can try running the program in Wine. But running on wine depends on the compatibility of the program itself.

---

### Post by Paulgirardin on 2014-11-13
Both dual boot and wubi require you to reboot.Running windows in a Virtual machine within Ubuntu does not require a reboot.

---

### Post by Impavidus on 2014-11-13
... But if you use a virtual machine you would be running Ubuntu and Windows at the same time (although not all the time, only when you need the virtual system), so you need a more powerful system. Speaking of which, you haven't told us the specs of your computer yet.

---

### Post by ian-weisser on 2014-11-13
I think you are asking to do very complex, risky actions to install Ubuntu and cross-platform compatibility.
That seems quite unwise if you really need your Windows and data available without any breakage.

If you really need your applications and data, like you claim in Post #1, and you are not an experienced Linux user, then I recommend that you DON'T BREAK YOUR WINDOWS on the mere hope that Ubuntu will be better. Don't dual-boot. Don't repartition. Those are risky actions.

1) Make sure your data is backed up.
2) Make sure you have a Windows restore media created...and you know how to use it.

Now you are ready to start.

3) Install cross-platform, Linux-compatible applications onto your Windows. Use them instead of Word and others. Get a feel for what you really, absolutely need from Windows. This might take you days or weeks.

4) Install Linux onto an external drive or USB stick, NOT your hard drive. Boot into that. Try it. It may be slow if you're not using USB3.0. That's your experimental install. Try Wine and a VM there. See if they do what you need them to do.

After you complete Step 4, you will have a much better idea of what you want, what you are capable of doing (and fixing), and what your next step should be.

---

### Post by monkeybrain20122 on 2014-11-13
If you have a spare external hd create an ext4 partition and make a full install of Ubuntu in it. You can use it like a native install when you boot it up your laptop. Flash rive will be slow but an external hd will give you native speed whether you have usb3 or 2 (excpet maybe booting and moving files back and forth)

---

### Post by Impavidus on 2014-11-13
++ to the previous posts. Installing on an external drive is a good way if you're worried that you may damage your existing Windows install (which Windows version?). You can even (temporarily) disconnect the Windows drive to be really sure you don't damage it. Not saying that installing Ubuntu on the same drive as Windows is terribly hard, but if you're worried, you can just use an external drive.

---

### Post by Impavidus on 2014-11-13
No, wubi is no longer supported. But whether you use wubi or not has no influence on wine (you know, the drink you make from the fruit of the vine). Whether you can run the Windows program this way depends on the program being portable enough that you can move it from one system to another without reinstalling and even then, success in wine is never guaranteed.

---

### Post by grahammechanical on 2014-11-13
I am not entirely clear on what you want to do but I do know that with Wine the Windows program has to be installed in Wine. Wine comes with an Add/Remove programs dialog that lets us browser Windows style to a Windows install exe and then the program will install inside the Wine folder/directory structure that replicates the Windows folder/directory structure.

Once the Windows application is installed then it is launched from an icon just like any Linux application in Ubuntu but Wine takes care of the loading of the application. If you are thinking of loading Wine and then directing Wine to run a Windows  program installed on a Windows partition/drive, then I would say the Wine is not designed to do that.

Regards.

---

### Post by sandyd on 2014-11-13
Please dont create multiple threads on the same topic as it dilutes community effort and makes it confusing for those trying to help

Thanks!

Oh, and threads merged.

---

