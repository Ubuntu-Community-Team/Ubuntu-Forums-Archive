---
title: "Access Denied for subdirectories on /var/www/"
date: 2007-09-25
forum: General Help
---

### Post by jonbey on 2007-09-25
Hello

I am a total Linux noob, so please bear with me. Last night I installed Apache and PHP on my Ubuntu, then created a static index.html in /var/www/ and viewed it OK at [http://localhost/](http://localhost/) so went to bed happy.

This evening I tried to copy website files to /var/www/ and got a permissions problem, so I did this (read it on some random webpage that I Googled):

chown -R jon /var/www/

This allowed me to copy over all my files fine, but when I went to view them, I got an access denied message. So I then did this:

chmod -R 755 /var/www/ which worked OK for the index file and everything else in www (I think that this is what I did, I did not record this step....)

However, subdirectories still have the permission denied error. I googled again, and came up with this:

root@jon-desktop:/var/www# chmod -R 755 *.*

which did nothing noticable, so I followed it with 

root@jon-desktop:/var# chmod 755 www

and still no change.

Also, my files require me to parse php in html files, for which I have the required code in an .htaccess file. But this is also not working. For now I hope it too has something to do with permissions, but somehow I think that it may be another problem.

So, what do I need to do to gain permission to view subdirectories? 
I have heard people mention groups, but as yet I have not read up on this, so am a bit lost. 

Cheers,

Jon.

PS. I am logging everything I do my blog: [http://www.webologist.co.uk/](http://www.webologist.co.uk/)
I even copied all the output when I installed Apache and PHP, so if there are odd variations depending on Linux distro, Apache version, or whatever else, hopefully the info is there!

---

### Post by jonbey on 2007-09-25
I think that I found the solution, or at least a solution (it does not seem ideal).

I typed this:

sudo chmod -R 755 ./articles

and it works. 

But, this leads to questions:

1. There must be one command to change permissions for all subdirectories?
2. why ./articles and not just articles? When using chmod on my webhost server, I never typed ./ to change permissions for a directory (I use Jumpline.com if that helps at all).
3. Most important question - is this the correct thing to do, or are there security risks once I go online with my website? Security is something that I know nothing about (yes, even less than I know about Linux in general!) and I keep seeing threads about it, which worries me.

Cheers

Jon.

---

### Post by jonbey on 2007-09-25
Another problem solved! I found the Ubuntu help pages for enabling .htaccess:
[https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)

and this solved the problem, everything is working now!

Thanks for your speedy replies!

---

