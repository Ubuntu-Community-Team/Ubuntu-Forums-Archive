---
title: "openoffice slow startup"
date: 2006-12-03
forum: General Help
---

### Post by dubrict on 2006-12-03
Hi, I just thought I'd post this to give people some help.  I had a problem with openoffice taking forever to load on my 64bit installation.  After searching and searching the forums, everybody pointed at the quickstarter, which doesn't help.  It takes the same amount of time to load from the quickstarter (over a minute.)

The way to fix it is by going into the options for openoffice and disabling java.

So, if there's anybody else looking for a solution to this problem and is being frustrated by everybody thinking it's the quickstarter, here you go.

And if anybody knows how to make it work faster *with* java, please let me know.  Thanks!

---

### Post by laidback on 2006-12-03
Gave this a try and yes it does speed things up a bit. I never had quite the time problem where it took > 1min but it's now even quicker. Empty WP 10 secs, empty Spreadsheet 10 secs. WP document 13 secs, Spreadsheet document 22 secs ( quite a large document). 

I'm running on an old recyled AMD Athlon XP running at 1.5Ghz, 768 Mb RAM, onboard graphics, nothing special at all. Ubuntu Dapper Drake with all updates.

Thanks for the tip.

Laidback

---

### Post by ahok on 2006-12-12
Try This :

Tools-Options-OpenOffice.Org-Memory --> Enable systray quickstarter

Hope this can help ...

---

### Post by greviant on 2006-12-12
Another thing you might do is try using the 32-bit Java Virtual Machine as you default.

Sun designed the 64-bit JavaVM with servers in mind, so it is slower than the 32-bit JavaVM but supposedly produces more stable code on compile, and less errors at runtime.  I've done this on my Athlon 64 2800+ in the past (currently running 32-bit edgy) and seen an improvement in load time.  If you aren't using the Sun JRE, or are not willing to sacrifice 64-bit then the quickstarter or disabling Java is the best idea.

---

### Post by dubrict on 2006-12-12
well, it turns out having the blackdown VM installed and enabled for use allows it to load a lot quicker.. I'm using that now, and it takes less than 3 seconds to load openOffice.

But is there an explanation for why it takes so long when no VM's are installed?  Does openOffice search the computer for a virtual machine when you start it up, if none are explicitly enabled in the options?

---

### Post by rajeev1204 on 2006-12-12
hi

 i think we have created the first bloatware for linux with openoffice

its just too monstrous now

btw , i have shifted to abiword and gnumeric :) 

they are super fast compared to that openoffice crap

hey dubrict , i thought u were using 32 bit ubuntu edgy!

regards

rajeev

---

### Post by hikaricore on 2006-12-12
> **dubrict said:**
> 
The way to fix it is by going into the options for openoffice and disabling java.

Nice tip :)  I may now finally get some use out of the OOo applications.

---

### Post by dubrict on 2006-12-12
I was actually thinking about trying out abiword earlier today.. I really don't use anything but the text editor in openoffice, and the spreadsheet tool just needs work.

I use 64-bit edgy on my computer, but I also maintain a computer lab with 32-bit machines.  I had edgy on those for a little while, but chose to drop it back down to dapper because, well, it was a lab and it needed more stability.

I agree with you about the bloatware... it's starting to remind me of the Nero application suite for windows.  Or the new AOL messenger.

---

### Post by gilgy on 2008-03-27
This post may be too late, but I think it works....

Look for the pspfontcache in the open office folder (it should be under home), and then delete it. Launch open office to generate a new pspfontcache file on the same location. go back to the pspfontcache and change the permission to read only. Got this solution from another forum, and it works great for me....

---

