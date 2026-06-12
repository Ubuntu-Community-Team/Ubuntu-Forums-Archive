---
title: "Internet Explorer on Linux"
date: 2007-11-13
forum: General Help
---

### Post by namich2007 on 2007-11-13
Hi all,

I am a member of an IT team administering a university network infrastructure. At this university we use a software for administering internal exams to students.Unfortunately,it only to  work with internet explorer, and the developers are not to keen on making that software more versatile.

I want to convert the testing center PCs to run Linux,preferably Ubuntu Linux.However the fact that I need internet explorer as the default browser has been the limiting factor for me.

I have been searching for solutions and have found three possible answers; 

A) Install Wine then install IE 6.0 from wine
B) Install Crossover and then install IE 6.0 
C) Install IE4Linux 

I First installed Wine, which installed perfectly. however the IE 6.0 installed choked half way when it was downloading the necessary files from the web.

I then installed IE4Linux,which again installed fine,however when it came to the point where it started the initializing of IE 6.0, it barfed an error message about "unable to extract CAB files".

The third try with Crossover,also installed fine ,but it again choked when downloading files from Microsoft website.

I am no newbie when it comes to Linux (not a Guru either :)), but I have successfully fiddle my way in Linux from since Red hat 7.3 to know what I am doing. However this problem baffles me, in that so many other members in this forums have had success in one way or the other with all the above applications.

I would really appreciated all the help I can get.

I run Ubuntu 7.10 on HP laptop ZE4947wm-b     
1.6MHz, 768Mbs ram

and 

Open Suse 10.3 on Intel board D865 Perl workstation
3.0 Mhz, 1gig ram



can any one shed some light to this problem.

Thanks for you all time

---

### Post by renzokuken on 2007-11-13
i used ie4lin fine, the cab extract problem may be due to not having cabextract installed

run

```
sudo apt-get install cabextract
``` then try again

---

### Post by RHTopics on 2007-11-13
The October issue (83) of Linux Magazine has an article on installing and using IEs4Linux.  In the article there is a troubleshooting guide which has the following advice:

    Your problem could be associated with a failure to download packages.  Their solution is to manually download packages and place them in the directory "~/.ies4linux/downloads".

    Second solution is to solve the problem of the DNS server not finding the IP address for "download.microsoft.com".  They suggest doing a ping on "download.microsoft.com", copying down the IP address that is returned, and then creating a new entry in your "/etc/hosts" file for that IP address.  For me that would be this new entry:

    84.53.175.169  download.microsoft.com

Another thought, have you considered going virtual.  That is using something like QEMU and install Windows in a virtual environment for just the purpose of running Internet Explorer.  That could actually be the safest way to do it.

---

### Post by namich2007 on 2007-11-13
[QUOTE=renzokuken;3762687]i used ie4lin fine, the cab extract problem may be due to not having cabextract installed

I have cabextract installed before as directed by this tutorial="http://www.tatanka.com.br/ies4linux/page/Installation"]http://www.tatanka.com.br/ies4linux/page/Installation[/URL]


RH... I have considered going virtual. In fact I do have a virtual XP on my personal HP laptop at the moment.However the reason for wanting to migrate to linux completely is to avoid Microsoft licensing crap.So running Windows guest on a linux host on the university system still obligates the university to have a license for this purpose. So this doesn't help me at this moment.

However I am going to look at your other suggestion

Thanks you all

namich2007

---

