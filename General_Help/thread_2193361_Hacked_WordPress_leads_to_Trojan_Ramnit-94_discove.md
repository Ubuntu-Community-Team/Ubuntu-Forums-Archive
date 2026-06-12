---
title: "Hacked WordPress leads to Trojan Ramnit-94 discovery"
date: 2013-12-12
forum: General Help
---

### Post by sprintexec on 2013-12-12
I have a number of WordPress (WP) installations with Bluehost. Today they advised me that at least one of my installations has been hacked. They suggested that I scan my laptop to check for any possible issues. Whilst I did not expect to find anything clamav found and reported these: 
> /home/sprintexec/.wine/drive_c/users/sprintexec/Temp/ilivid.7zTrojan.Ramnit-94         
/home/sprintexec/.wine/drive_c/users/sprintexec/Local Settings/Temporary Internet Files/Content.IE5/87UKECR2/ilivid[0]..7z      Trojan.Ramnit-94         
/home/sprintexec/.wine/drive_c/users/sprintexec/Local Settings/Temporary Internet Files/Content.IE5/CE8XHVNN/ilivid[0]          Trojan.Ramnit-94  
I have searched to see if anyone else has had a similar experience but can find nothing. Does anyone know what problems if any these reports pose. I use ubuntu 12.04LTS and Firefox 26 is my default browser. Although I have wine installed, I seldom use it. 
Any help that community members can offer will be much appreciated! 

The next issue is cleaning up my WP installs. I have looked at my log files and it looks like the exploit is via wp-admin as all of my installs are up-to-date and I have removed all themes except Twenty12 and Twenty13 and have removed all plugins.  Again any help that community members can offer will be much appreciated!

---

### Post by SeijiSensei on 2013-12-12
The trojan is sitting in your .wine subdirectory, probably because you used a version of IE there.  Whether it came from your own WordPress site is an open question.  It's [not something]("http://arstechnica.com/business/2012/01/part-virus-part-botnet-spreading-fast-ramnit-moves-past-facebook-passwords/") you want to have on your computer, though.

I recommend simply blowing away /home/sprintexec/.wine.  It will be rebuilt automatically if you need to use WINE in the future.  The only drawback would be if you have a lot of Windows software installed under WINE.

I have a suggestion on my WP site to upgrade to 3.8.  I'm going to do that now.  Perhaps you should do the same.

---

### Post by sprintexec on 2013-12-12
> **SeijiSensei said:**
> The trojan is sitting in your .wine subdirectory, probably because you used a version of IE there.  Whether it came from your own WordPress site is an open question.  It's [not something]("http://arstechnica.com/business/2012/01/part-virus-part-botnet-spreading-fast-ramnit-moves-past-facebook-passwords/") you want to have on your computer, though.

I recommend simply blowing away /home/sprintexec/.wine.  It will be rebuilt automatically if you need to use WINE in the future.  The only drawback would be if you have a lot of Windows software installed under WINE.

I have a suggestion on my WP site to upgrade to 3.8.  I'm going to do that now.  Perhaps you should do the same.

Thank you SeijiSensei for your swift, helpful advice. :KS

I like the idea of blasting wine. It has been nothing but a pain. I had used it for kindle (which I now access via the cloud reader when I'm not using my kindle reader) I also tried to use wine for an itunes workaround which turned into a ball of chalk. So yes, it will be bye bye wine! 

As to the WP issues I'm grinding my way through an incomplete list of malicious content provided by my hosting firm - Bluehost. However trying to figure what part of a .js file is valid or not is challenging to say the least! Sadly the upgrade route is now close off until I satisfy Bluehost that my domains are squeaky clean.

---

### Post by Habitual on 2013-12-12
[http://www.unmaskparasites.com/security-report/?page=domain.com](http://www.unmaskparasites.com/security-report/?page=domain.com)
and be attentive to "External References" on the report.

Can also scan domain.com at [http://wepawet.cs.ucsb.edu/](http://wepawet.cs.ucsb.edu/)

---

### Post by sprintexec on 2013-12-13
> **Habitual said:**
> [http://www.unmaskparasites.com/security-report/?page=domain.com](http://www.unmaskparasites.com/security-report/?page=domain.com)
and be attentive to "External References" on the report.

Can also scan domain.com at [http://wepawet.cs.ucsb.edu/](http://wepawet.cs.ucsb.edu/)

Thank you Habitual, :KS

These resources look useful. However I am unsure how I can use them at this time since Bluehost have blocked web-access to my account. 

I have been able to download all of my sites so I have a folder labelled 'hacked' with about 750Mb of WP scripts and my data sitting there contaminated waiting for me to figure out my next steps.   

More coffee and more time required ;)

---

### Post by SeijiSensei on 2013-12-13
My advice would be to create a virtual server using something like [VirtualBox]("http://www.virtualbox.org/") or VMWare and install the [lamp-server]("https://help.ubuntu.com/community/ApacheMySQLPHP") "task."  Then install a brand-new copy of WordPress and copy over only your themes and any uploaded images, etc., from the existing /wp-content/ directory.  Look carefully at the files there to make sure you only copy ones you recognize.  For instance, I only upload images into /wp-content/uploads/, so anything else there would be highly suspect.  Finally, use [mysqldump]("http://www.thegeekstuff.com/2008/09/backup-and-restore-mysql-database-using-mysqldump/") to create a plain-text dump of the blog's database and read it into the MySQL instance on the virtual machine. See if that results in a working site. 

WordPress puts all the textual content into the database, which makes it easier to replace an instance of WordPress with a new clean copy.

I'm curious.  How are you supposed to demonstrate to Bluehost that your site is clean?  Do they have some kind of scanning software that looks for dangerous things on WordPress sites?

BTW, just out of curiosity I ran clamscan against my website directories.  It only found the copy of the [EICAR test file]("http://www.eicar.org/85-0-Download.html") that I leave there to test antivirus implementations.  Have you scanned the copy of the website that you have?  Anything bad show up, like copies of that trojan?

---

### Post by sprintexec on 2013-12-14
Hi SeijiSensei, 

Again thank you for your valid helpful pointers. I'll respond to them out of sequence if I may. 

"I'm curious. How are you supposed to demonstrate to Bluehost that your site is clean? Do they have some kind of scanning software that looks for dangerous things on WordPress sites?"

Bluehost are running some kind of scanning software that appears to look for, amongst other things, code in unexpected places. When they identify 'issues' they email the account holder. The email that I received said simply that my account was being suspended for a 'Terms of Service' infringement. As WordPress is so popular with people it is a target for various malware. Plugins and themes add to the opportunities. I should also mention that I did not identify the risk of having quasi-redundant sites languishing on my account. Whilst I was ignoring them they were being hacked. When I contacted support staff at Bluehost they were helpful. They ran a report which listed files which 'appear to contain malware'. From here on it  is up to the end user to decide how to proceed. It is perhaps worth mentioning that with a couple of the scripts that were running on my account (PmWiki), the Bluehost software came up with false positives. The 'clean up' has taken the better part of a day and I have learned to be more cautious. 

"BTW, just out of curiosity I ran clamscan against my website directories. It only found the copy of the EICAR test file that I leave there to test antivirus implementations. Have you scanned the copy of the website that you have? Anything bad show up, like copies of that trojan?" 

Thank you, this is a great tip, one that I hadn't and probably wouldn't have thought of myself :(. I'll check it out. :)

Finally - I like the idea of setting up a virtual server but I'm concerned about the time that it would take me. With Christmas coming up and flights to UK to see family and friends that may be something that I approach in January '14.

---

### Post by sprintexec on 2013-12-14
> **sprintexec said:**
> Thank you Habitual, :KS

These resources look useful. However I am unsure how I can use them at this time since Bluehost have blocked web-access to my account. 

I have been able to download all of my sites so I have a folder labelled 'hacked' with about 750Mb of WP scripts and my data sitting there contaminated waiting for me to figure out my next steps.   

More coffee and more time required ;)

Update - Habitual,

Now that Bluehost have unblocked my access to my sites I have had great pleasure in testing using the resources that you mention. I've also book marked them as they are useful tools to have available.

---

### Post by coldraven on 2013-12-14
You can download a ready made VirtualBox Ubuntu server from here:
[http://virtualboxes.org/images/](http://virtualboxes.org/images/)

Then just add the LAMP with "tasksel", see here:
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

Have a stress free Christmas :)

---

### Post by sprintexec on 2013-12-14
SeijiSensei / coldraven ,

To run a Virtual Box Ubuntu server what would I need in terms of hardware? I have an old lightly used Pentium 4 with 12.04LTS as its OS. Would this suffice? :-)

---

### Post by SeijiSensei on 2013-12-15
You need at least 2 GB of memory for a machine to run smoothly and host a VM.  You could get by with a bit less if you install Ubuntu Server in the VM since it does not have a GUI.  I can run Server in 512M.

---

### Post by Habitual on 2013-12-16
> **sprintexec said:**
> Update - Habitual,

Now that Bluehost have unblocked my access to my sites I have had great pleasure in testing using the resources that you mention. I've also book marked them as they are useful tools to have available.

It's a "Keeper".

---

### Post by SeijiSensei on 2013-12-16
> **sprintexec said:**
> SeijiSensei / coldraven ,

To run a Virtual Box Ubuntu server what would I need in terms of hardware? I have an old lightly used Pentium 4 with 12.04LTS as its OS. Would this suffice? :-)

Don't bother with a virtual machine; just install the "LAMP" task on that box like this:

```

sudo apt-get install tasksel
sudo tasksel

```

You'll be presented with a menu of options.  Pick the "LAMP Server" item, then tab to OK and hit return.

Once everything is installed you can continue by following the discussion here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP).

---

