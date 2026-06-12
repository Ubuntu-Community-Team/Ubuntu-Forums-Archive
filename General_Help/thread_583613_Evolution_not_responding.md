---
title: "Evolution not responding"
date: 2007-10-20
forum: General Help
---

### Post by OldDog11 on 2007-10-20
I have been using Evolution for several months now but it has suddenly decided to "lock up" on me.

No functions at all are available to use except the close program. This then informs me that the progam is not responding and offer me the option to force a quit.

Re-starting or shutting down and restarting has no effect.

Can anyone help please?

---

### Post by bapoumba on 2007-10-20
Any error running **evolution** from a terminal ?

---

### Post by OldDog11 on 2007-10-20
I do not know ow to do that, I am trying to find out but no luck yet.

---

### Post by bapoumba on 2007-10-20
Please open a Terminal (> Accessories > Terminal) and run:
```
evolution
```
Paste the complete output in here.

---

### Post by OldDog11 on 2007-10-20
Evolution still not responding - output from terminal as requested:

CalDAV Eplugin starting up ...

(evolution-2.10:10692): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:10692): e-utils-WARNING **: Plugin 'Spamassassin junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.10:10692): DEBUG: mailto URL command: evolution %s
** (evolution-2.10:10692): DEBUG: mailto URL program: evolution

---

### Post by bapoumba on 2007-10-20
Are you using an imap account ?

---

### Post by OldDog11 on 2007-10-20
I don't think so but what is an imap account?

---

### Post by bapoumba on 2007-10-20
It's a mail protocol, so I assume you are using a pop account?

---

### Post by OldDog11 on 2007-10-20
Yes - i have a pop account

---

### Post by OldDog11 on 2007-10-20
Does anyone know how I can resolve this problem please? I do not know how to get my emails working again.

---

### Post by bapoumba on 2007-10-20
Hmm, many different issues come up in a search with these errors.
Any huge attachement in a file with > View >  Preview > Show messages ticked ?
There is a bug with big attachment files in feisty.

---

### Post by OldDog11 on 2007-10-20
I think that the mail it locked up on may have contained a large file, is there anyway I can get around this bug?

---

### Post by bapoumba on 2007-10-20
Yes, but I cannot guide you through, I do not have gconf-editor.
So in open gconf-editor, you should have a menu for evolution (under desktop, probably), where you can untick the preview for attachments.
Once done, open evolution again, delete the file in the folder, and purge the deleted file.
If that is the problem, it should be solved.

---

### Post by OldDog11 on 2007-10-20
Thank you for your help but now I am getting a little lost.

I do not know what you mean by open gconf-editor, I cannot find this on my desktop as you suggest.

---

### Post by bapoumba on 2007-10-20
Can you get it entering **gconf-editor** in the terminal?
Are you using GNOME desktop?

---

### Post by OldDog11 on 2007-10-20
I have found it and unticked the show preview box. I have re-booted but evolution is still not responding. Do you know of anything else I can try?

---

### Post by bapoumba on 2007-10-20
Not really.
What is the output to the last command:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
(the dist-upgrade one).
You'll have to enter your password, it won't show up on screen, just hit enter after you've typed it.

---

### Post by OldDog11 on 2007-10-20
If I enter the following as you suggest am I right in thinking that it will upgrade me to Gutsy? I was not planning on upgrading just yet, I want to make sure there are no issue with the upgrade.

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by bapoumba on 2007-10-20
No no, it won't upgrade to gutsy. If you still have feisty in your sources.list, it will upgrade more thoroughly the packages within you own release, checking the dependencies more carefully.
If you are not sure, paste your sources.list first, we'll have a look:
```
cat /etc/apt/sources.list
```

---

### Post by OldDog11 on 2007-10-20
Response from sources list

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by bapoumba on 2007-10-20
Yes, it's fine. Please run the dist-upgrade (and I'm still looking.. sorry)

---

### Post by OldDog11 on 2007-10-20
Result from dist-upgrade.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by dcstar on 2007-10-20
Try this procedure:

[LIST=1]
[*]Disconnect from the Internet (so you don't download mail)
[*]Rename your (hidden) .evolution directory and then try and restart Evolution - that should create a new environment for mail files and if it works you know you have some corrupted files which are causing the problem
[*]If things still didn't work, then rename the newly created .evolution directory to something else, and then rename your original directory back to .evolution[/LIST]

---

### Post by OldDog11 on 2007-10-21
Thanks
I have renamed my evolution directory and evolution now starts up and is working. It is of course now empty and a completely fresh start.

Is there anyway I can now repair the original directory or recover my "lost" mail and settings?

---

### Post by dcstar on 2007-10-21
> **OldDog11 said:**
> Thanks
I have renamed my evolution directory and evolution now starts up and is working. It is of course now empty and a completely fresh start.

Is there anyway I can now repair the original directory or recover my "lost" mail and settings?

All the mail and folders are in the original directory, you can copy them across to the same place one by one and keep restarting Evolution until you find the one(s) that breaks your system - then you know to leave that one alone!

Make a copy of your new .evolution directory before you do any of this so you have a copy of all the working stuff to quickly restore if you need it.

With a bit of luck you may lose nothing at all.

---

### Post by OldDog11 on 2007-10-21
I have tried to find my mail in the original directory but I do not know where it is. Can you direct me please.

---

### Post by dcstar on 2007-10-21
> **OldDog11 said:**
> I have tried to find my mail in the original directory but I do not know where it is. Can you direct me please.

.evolution/mail/local

---

### Post by OldDog11 on 2007-10-21
Sorry - I can be all fool sometimes! I was looking in the new .evolution and not the old .evolution file.

I have now found my data. I will let you know if I suceed in recovering it - thanks.

---

### Post by OldDog11 on 2007-10-21
Hello David

Many thanks for your help - I have now recovered all of my data and deleted the corrupted mail.

Evolution is now working again!

Keep up the good work - the support from people like you is terrific, once again many thanks.

---

### Post by bapoumba on 2007-10-21
Many thanks dcstar :)

---

### Post by Ubluzok on 2008-04-16
Hello friends, I had the some problem but I resolved it by other way:

I'm using Ubuntu Hardy, and automatically get all off updates. But from 15April evolution become freeze in startup, only close button is working.

When I tried to run in throught console, I read:
> 
ubluzok@notebook13:~$ evolution
evolution-shell-Message: Killing old version of evolution-data-server...

Then i saw, theat I have evolution-data-server-22 running, I've made:
> 
ubluzok@notebook13:~$ killall evolution-
evolution-alarm-notify      evolution-data-server-2.22  evolution-exchange-storage
ubluzok@notebook13:~$ killall evolution-data-server-2.22
ubluzok@notebook13:~$ killall evolution-data-server-2.22
ubluzok@notebook13:~$ killall evolution-data-server-2.22
evolution-data-server-2.22: &#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1089; &#1085;&#1077; &#1091;&#1073;&#1080;&#1090;


Only after third killall It was killed, but maybe it just need time to stop.  remarqu: CPU usage wery low and about 1%-3%

Now the evolution starts correctly.

P.S. I'M using IMAP and POP stores, Compiz, ustable releases, My book is Sony Vaio VGN-SZ6RXN . If somebody need additional information feel free to ask me.

---

