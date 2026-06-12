---
title: "Internal Webmail server - suggestions?"
date: 2005-10-24
forum: General Help
---

### Post by scalez on 2005-10-24
Good day!

Well folks, i'm a newly registered user, and why did i register? i finally couldn't find the answer i was looking for, soo, here we go!   i work for a k-12 school district as one of the "computer guys" focused mainly on windows machines.  like so many bosses do, mine had an epiphany and told me to basically "make it work."

the idea goes like this: we would like to institute a separate e-mail environment for student use only (e.g. students.district.org) for the students to use to communicate with other students and with faculty.  this would be using a webmail interface, and possibly accessible from outside the network via a webmail interface, but unable to send and receive messages to address that are not either @district.org or @students.district.org.  on top of that, i got the, "and try to do it for little or no cost, as we didn't budget for it."

weee.

i've got an old dual pIII 650 server that is still serviceable, and had 2k server on it that is going to be my little donor.  i'm still a windows guy, as that's what i work on, but so far, i've only dabbled in Linux. i've found [Hmail]("http://www.hmailserver.com/") which i could install on windows, and i've also found a Ubuntu/ Hula that i thought i'd try.   my biggest concern is ease of administration, as i will not be the only one over the box, and some of my co-workers are greater neophytes that i.

any suggestions or guidance is greatly appreciated.

kevin

---

### Post by scalez on 2005-10-24
bump

any ideas, or am i on the right track?

---

### Post by Saiboogu on 2005-10-25
Sounds like you're on the right track. I wanted to get email (imap and webmail) running for personal use on a home server.. After bashing my head against courier-imap, postfix, sendmail, fetchmail ... argh ... configs for awhile, I tried this tutorial: [VHCS.]("http://www.ubuntuforums.org/showthread.php?t=25722&highlight=vhcs")

Its not quite what either of us are looking for (if you've ever rented commercial webhosting, VHCS is a free version of the popular cPanel admin tool). Basically, once you run the script, you have a webpage you visit, sign in - create a user account (in its real use, this would be a customer of your hosting service), and within that user account you can easily setup a basic email server, web server, webmail -- etc. I used that for a start, and since then I've been picking apart the prebuilt configs to try and learn how to do it on my own.

Caveats: If you're using Breezy, modify the script from that link, replace any instance of hoary with breezy. Also, look for improperly wrapped lines in the section where the script writes your sources.list. Its well commented, you'll find the section easy enough. And make a backup copy of /etc/apt/sources.list first! This script tampers with it, and even with the fixes I did, still fouled it up good - script ran, but regular updates would have been broken if not for the backup.

With all that said.. After I got this installed and running, I discovered Hula and have been tempted to give it a try. Looks to be a little closer to what I wanted (ie - single server solution for email, contacts, etc) than VHCS with its virtual hosts and reseller accounts. If you setup Hula, please report on your experience!

---

### Post by scalez on 2005-10-25
ok, i just keep feeling like a newbie all over again.  i over research, and then have way too much stuff in my head . . . then i go set the darn thing up and it's seamless.

i'll just have to see how the install goes, and see if anyone else has any better suggestions.

---

### Post by Mr. Electric Wizard on 2005-10-25
I use postfix for pop3/smtp email and it works like a champ!
Squirrel mail works great for webmail too!

---

