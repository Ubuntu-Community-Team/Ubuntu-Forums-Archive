---
title: "Changing cups-pdf Directory"
date: 2007-11-29
forum: General Help
---

### Post by skattman83 on 2007-11-29
I'm trying to use cups-pdf to create pdfs and it works just fine until I go into 
/etc/cups-pdf/cups-pdf.conf and change the path.  No matter what I change it to I get ```
Thu Nov 29 17:11:55 2007  [ERROR] failed to set file mode for PDF file (non fatal) (/home/rayarnold/Ubuntu_Forums_-_Search_Results.pdf)
```.  If I change it back to the default, it work properly again.  All I want to do is change the path from {home}/PDF to {home}/Documents, but it doesn't work.

---

### Post by ShodanjoDM on 2007-11-29
Just an idea, but how about deleting the PDF folder and creating a link to {home}/Documents in {home}/ then name it as PDF?

---

### Post by skattman83 on 2007-11-29
That would be acceptable as a last resort, but it seems kind of hack-ish.  I'd prefer to get cups-pdf working properly.

---

### Post by erginemr on 2007-11-30
Hello,

The folllowig thread also discusses this problem:
[http://ubuntuforums.org/showthread.php?t=89677](http://ubuntuforums.org/showthread.php?t=89677)

I also tried to change the default directory in:
/etc/cups/cups-pdf.conf  (the line "Out ${HOME}/PDF")
to something else but could not succeed.

This is probably a bug in the cups version we are using, so I believe, we should live with it.

---

### Post by noynac on 2007-11-30
The situation is a bit different, but you may want to look at the following bug report:

[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/147551](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/147551)

Some people were able to change the directory, but I never could and finally just gave up. If running Gutsy, did you change the apparmor file?

---

### Post by skattman83 on 2007-11-30
> **noynac said:**
> The situation is a bit different, but you may want to look at the following bug report:

[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/147551](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/147551)

Some people were able to change the directory, but I never could and finally just gave up. If running Gutsy, did you change the apparmor file?

I am running Gutsy, but what is apparmor?

---

### Post by noynac on 2007-11-30
> **skattman83 said:**
> I am running Gutsy, but what is apparmor?
I do not have sufficient knowledge to explain apparmor, but it's security software, and you can read about it in this article:

[http://en.wikipedia.org/wiki/AppArmor](http://en.wikipedia.org/wiki/AppArmor)

The directions for making the necessary changes to the apparmor file are in the bug report.

---

### Post by mannheim on 2007-12-05
> **noynac said:**
> The situation is a bit different, but you may want to look at the following bug report:

[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/147551](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/147551)

Some people were able to change the directory, but I never could and finally just gave up. If running Gutsy, did you change the apparmor file?

That worked for me. My steps were:
[LIST=1]
[*]Edit /etc/cups/cups-pdf.conf to change the default "Out" directory to ${HOME}/Desktop
[*]Edit /etc/apparmor.d/usr.sbin.cupsd as described in the above [launchpad posting]("https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/147551/comments/3")
[*]Reload apparmor profiles using "sudo invoke-rc.d apparmor reload"
[*]Restart cups using "sudo invoke-rc.d cupsys restart"
[/LIST]
(I don't know if restarting cups was needed.)

---

### Post by noynac on 2007-12-05
> **mannheim said:**
> That worked for me. My steps were:....

I followed these steps and now my PDF files are saved to the directory of my choosing. I could have sworn that I tried this exact same procedure before; perhaps I did not run the two reload commands. 

Anyway, thanks for the posting. It's nice to get this fixed.

---

### Post by skattman83 on 2007-12-06
I tried it as well, and it works great now.  Thanks for the help.

---

### Post by poccino on 2008-02-12
> **mannheim said:**
> That worked for me. My steps were:
[LIST=1]
[*]Edit /etc/cups/cups-pdf.conf to change the default "Out" directory to ${HOME}/Desktop
[*]Edit /etc/apparmor.d/usr.sbin.cupsd as described in the above [launchpad posting]("https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/147551/comments/3")
[*]Reload apparmor profiles using "sudo invoke-rc.d apparmor reload"
[*]Restart cups using "sudo invoke-rc.d cupsys restart"
[/LIST]
(I don't know if restarting cups was needed.)

Can you please teach me how to do it step by step? I am an absolute beginner!
Thanks.

---

### Post by erginemr on 2008-02-12
Here are the steps in detail. You can copy and paste the commands from here to the terminal with Ctrl+Shift+V, or with right click and paste:

1. Open up a terminal first (Main Menu -> Accessories -> Terminal).

2. Write down:
```
gksudo gedit /etc/cups/cups-pdf.conf
```
to edit the file in question with Gnome Editor
Linux will ask for your root password. Enter your user password.

Find the lines:
```
### Key: Out
##  CUPS-PDF output directory 
##  special qualifiers: 
##     ${HOME} will be expanded to the user's home directory
##     ${USER} will be expanded to the user name
##  in case it is an NFS export make sure it is exported without
##  root_squash! 
### Default: /var/spool/cups-pdf/${USER}

Out ${HOME}/PDF 
```
and change the last line to
```
Out ${HOME}/Desktop 
```
Save and close.

3. This time, edit the second file with:
```
gksudo gedit /etc/apparmor.d/usr.sbin.cupsd
```

Find the lines
```
 @{HOME}/PDF/ w,
 @{HOME}/PDF/* w,
```
which are located at the end of the file. Change them to:
```
 @{HOME}/Desktop/ w,
 @{HOME}/Desktop/* w,
```
Save again and close.

4. Use the following command to reload apparmor daemon (= background service):
```
sudo invoke-rc.d apparmor reload
```

5. Use the following command to reload cups printer daemon:
```
sudo invoke-rc.d cupsys restart
```

That's all there to it.

---

### Post by lorenzosu on 2008-03-02
Hi,
Thanks for the very detailed instructions.

Desktop is quick and easy, but I was wondering if there is a way to actually be prompted (or to enter each time) the output for the PDF.

Bests,
Lorenzo.

---

### Post by phillywize on 2008-03-09
> **lorenzosu said:**
> Hi,
Thanks for the very detailed instructions.

Desktop is quick and easy, but I was wondering if there is a way to actually be prompted (or to enter each time) the output for the PDF.


Agreed.  This would be a fantastic feature, but I haven't seen a way to do it cups-pdf.  Which doesn't mean there isn't, but I'm not optimistic until cups-pdf gets a big overhaul from someone.

---

### Post by usolio on 2008-04-04
Great, instructions worked perfectly! Thank you.

---

### Post by neur0 on 2008-05-26
Tnx

---

### Post by floflooo on 2008-05-28
Worked for me too. It would have taken me forever to figure that thing out. Thanks!

---

