---
title: "Files wiped out by 13.04"
date: 2013-09-20
forum: General Help
---

### Post by wlg on 2013-09-20
I switched to Linux (Ubuntu) with version 7.04.  Upgrading each time up to 12.10 had no problems. Never lost anything and everything worked in the new upgrade.  Until 13.04.

I know I should back everything up before the upgrade but trusted the upgrade to not delete files since 7.04.  When I upgraded to 13.04 it wiped out 12.10 version OS and all of the files.  It left some of the older OS versions.

Searching the internet using remaining 10.04 a site recommended using Boot Repair Disk.  I burned the ISO on a CD, ran it as recommended and my boot then showed nothing but 13.04 and dozens of kernels.

I need help restoring 12.10 and lost files.

I am not a geek but I do find Linux friendlier than Windows.  I know no programming and to fix a problem in the terminal I need to copy and paste the entries which are very meaningless to me.

With these limitations in mind can anyone help me fix this problem?

Thanks in advance.

---

### Post by ibjsb4 on 2013-09-20
Save yourself some grief.  Burn a copy of 13.04 (live dvd), use it to retrieve your files and then do a fresh install.

In the future you may want to consider something like [Clonezilla]("http://clonezilla.org/") to clone your system before you do a version upgrade. Or in your case, maybe even better, move your [Home to its own partition]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=home+partition&sa=Search&cof=FORID:9").

---

### Post by wlg on 2013-09-21
How do I retrieve files by using a live DVD?

---

### Post by ibjsb4 on 2013-09-21
You access your HDD (Ubuntu partition) with it.

On the live dvd you have the option at boot to try Ubuntu without installing.  Do this, then pull up Nautilus file manager to access your HDD.  Then navigate to your home folder and copy your files to a flash drive or another HDD.

With any luck, it should go that easy.  Any questions?

---

### Post by wlg on 2013-09-21
OK, I am now using a 12.10 live DVD, would that work as well?

---

### Post by ibjsb4 on 2013-09-21
Yep, that will work.

---

### Post by wlg on 2013-09-21
OK, that being the case, if I open the home file I should see the files that I want to restore correct?

---

### Post by ibjsb4 on 2013-09-21
> **wlg said:**
> OK, that being the case, if I open the home file I should see the files that I want to restore correct?

Not sure what you mean by restore, but you will hopefully see your lost files and be able to copy them to another media.

---

### Post by wlg on 2013-09-21
Thanks but those files are empty, as I said I think 13.04 wiped them out.  That's what I meant by restore.  It seems they still must be on my HDD which is 1TB and not even close to capacity.  I need to find out how to recover them.

---

### Post by ibjsb4 on 2013-09-21
Do a search for them using Nautilus.

---

### Post by wlg on 2013-09-21
Maybe I'm not doing it right but for years now whenever I search for a file with words contained in the file name I invariably get the return: "File not found."  For images, I check the Showphoto File and it's empty, if the hundreds of images really don't have a name, how do I search for them?  Also if all of the files seem to be empty when I open them, how could I search for them?

I don't mean to be cute here. These are real questions.

This is really frustrating because the files must be on the HDD somewhere.  

Finding help elsewhere is frustrating because if you ask a real person, even a computer tech and you mention Linux their eyes glaze over and you feel like you are an extraterrestrial trying to talk to an earthling.

Thank you for staying with me.  Please tell me if I'm thinking wrongly on these things.

---

### Post by ibjsb4 on 2013-09-21
Ok, this has to turn up something.  For pictures try a search on **.jpg**

That should be the format you use for pictures.  

If this doesn't find anything, Im thinking your going to have to go with a recovery program for finding pics and files.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by wlg on 2013-09-21
OK,  I tried your suggestion and searched for jpg, none of my images appeared only jpgs from included apps in 12.10.  Also tried .NEF which is the raw photo format for Nikon, nothing.  Also tried .pdf, only test prints and manual, etc., none of my pdfs.

Can you make suggestions for apps  for  recovery program for finding pics and files?

---

### Post by Alxl on 2013-09-21
As last suggested by [**[COLOR=#000000]ibjsb4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1729120")  download and familiarize yourself with TestDisk/ The latest stable version is  6.14 /

You download it here : [www.cgsecurity.org/wiki/TestDisk_Download]("http://www.cgsecurity.org/wiki/PhotoRec")

---

### Post by ibjsb4 on 2013-09-21
I agree, we have tried simple recovery with no results.  Your going to have to go with recovery software.

---

