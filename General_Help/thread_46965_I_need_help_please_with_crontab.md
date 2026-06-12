---
title: "I need help please with crontab"
date: 2005-07-06
forum: General Help
---

### Post by dwaldie on 2005-07-06
Please help me, my brain feels like it going to explode.   I have been trying for 2 days to automate a simple script to automate my podcast downloading.  I have read, re-read, and re-re-read the man pages, done google searches, and searched this forum, only to become more frustrated.

Here is the script that I called podcast.sh and put it in /usr/bin
cd /home/dwaldie/jPodder/bin
./jpodder

That is it, I chmod a+x it, it is exicutable, I checked, and it works.

Now here is the frustrating part, as me, not root I type crontab -e and put the line...

30 2 * * * podcast.sh

I want it to start at 2:30 am everyday.

well, when 2:30 comes around and I am waiting, nothing happens.

So again, please help, since I shave my head, I have no hair to pull out.

Thank you very much,
David Waldie ](*,)

---

### Post by gil-galad on 2005-07-06
This might be a stab in the dark, but try putting it in like this:

30 2 * * * /usr/bin/podcast.sh

---

### Post by dwaldie on 2005-07-06
Nope that did not work either, I edited my crontab file to start it early to test.  Do I need to be root or reboot after changing my conrab file.

Thanks for the try
David Waldie

---

### Post by banadushi on 2005-07-06
First make sure cron is runnig:
```

$ ps -ef | grep cron

```

Also, why use the script at all why not just put:
```

30 2 * * * /home/dwaldie/jPodder/bin/jpodder

```

If it still does not work, then you can see the output of what happens when cron fires off by viewing your mailbox or if you want it to send to a remote mailbox, you can put:
```

MAILTO='address@example.org'

```
at the top of your crontab.  Personally I usually set the MAILTO variable to '' to prevent it from emailing me at all and filling up my mail spool on my workstation.

Have a good one!

jason

---

### Post by banadushi on 2005-07-06
So, yea I checked out this Jpodder software your trying to automate.  Not gonna work so hot dude.  Its a java app with a gui, so it natually requires X by default.  When cron fires it off, it fires off in a separate login that your one, therefor it does not have access to the X display,  I'm betting that the output of the cron proccess is somethign like:
```

cannot open display:

```

So its pretty much a hozer situation on the jPodder front.  If you want this automated you need to either get a console based podcast program, or one that allows non-X batch mode proccessing.

Sorry

Jason

---

### Post by dwaldie on 2005-07-07
Thank you for all the help so far.  I tried a little experiment  thanks to banadushi (thank you) creating a simple non gui script to delete a certain file, and it worked, but only when editing the roots crontab.  When I tried to edit my regular user crontab it did nothing.  How do I let my regular account use crontab?

Thank you all again for the help,
David Waldie

---

### Post by lothar_m on 2005-07-07
How do you reload the crontab file???

I use the following:

```

crontab -u user_x /home/user_x/scripts/mycrontab

```

this command will reload the file. I think it has to be done every time you change/edit the config file.

to check the changes use

```

crontab -u user_x -l

```

good luck

---

### Post by dwaldie on 2005-07-07
\\:D/   I would like to thank everyone for helping me with this problem.  It is finally working and crontab is great.  I have been so happy with Ubuntu, especially with this forum and all it's great help, support and advice.

Thanks again everyone,
David Waldie

---

