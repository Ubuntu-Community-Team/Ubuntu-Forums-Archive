---
title: "Help an SSH newb =)"
date: 2007-06-29
forum: General Help
---

### Post by herbster on 2007-06-29
I have ssh access with my website, I have about 300gb of space and I'd like to upload some of my files as backup and then weekly update them.

So say I have directory "stuff," I want to upload stuff to my server and using ssh every week I want it to connect/synchronize (don't know the term) so that for example if I have changed 1 file and added 2 new files in "stuff," only the changes will be uploaded of course, so it stays current every week.

I am aware of rsync and the --delete command I believe that does this, but I am clueless on how to put this all together. I have googled SSH and rsync and I'm not understanding the explanations.

If someone could give me simple steps or a guide in relatively plain language I'd love to learn and know how to do this, thanks!!

---

### Post by spin2cool on 2007-06-29
Do a little more googling.  I promise that there are some user-friendly guides out there.

Here's one that will give you the basics:
[http://lifehacker.com/software/rsync/geek-to-live--mirror-files-across-systems-with-rsync-196122.php](http://lifehacker.com/software/rsync/geek-to-live--mirror-files-across-systems-with-rsync-196122.php)

---

### Post by herbster on 2007-06-29
spin2cool,

Thanks, that was great help for the rsync command. I have also found:

[http://www.suso.org/docs/shell/ssh.sdf](http://www.suso.org/docs/shell/ssh.sdf)

Which I am using right now to set up my ssh connection and I am figuring this all out alas it seems :)

Hope anyone else can use these links to learn as I am.

---

### Post by tronica on 2007-06-29
You might consider sftp.

[http://www-acs.ucsd.edu/info/sftp.php](http://www-acs.ucsd.edu/info/sftp.php)

---

### Post by herbster on 2007-06-29
Okay I am trying to do the rsync with a test directory on my desktop called "stuff." I am using this command:

```
rsync -avz --delete ~/Desktop/stuff user@website.com/backup
```

I am getting this:

```
:~/Desktop$ rsync -avz --delete file user@website.com/backup
building file list ... done
rsync: mkdir "/home/user/Desktop/user@website.com/backup" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(529) [receiver=2.6.9]
rsync: connection unexpectedly closed (8 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(454) [sender=2.6.9]
:~/Desktop$
```

I cannot get this right, I've tried some combinations. I am just trying to upload the /Desktop/stuff directory to website.com/backup.

---

### Post by darrenm on 2007-06-29
I don't know rsync but that command is trying to create a dir called backup in a dir called [email]user@website.com[/email] which doesn't exist (You can't create 2 dirs at once)

---

### Post by tronica on 2007-06-29
try 

> rsync -a /source /destination

---

### Post by herbster on 2007-06-29
I figured it out, it was the / that should be a :, this is what to use:

```
sudo rsync -avz --progress /home/user/Desktop/file login@website.com:backup
```

This uploads /Desktop/file directory and all inside to website.com/backup. This is great! :D

---

### Post by qpieus on 2007-06-29
Good job on figuring it out, I was just about to correct your syntax there and you beat me to it :)

---

### Post by herbster on 2007-06-29
> **qpieus said:**
> Good job on figuring it out, I was just about to correct your syntax there and you beat me to it :)

Hehe, yeah I just noticed that because I just learned ssh a moment before rsync and the colons were there :)

I am still wondering though, how do I exclude subdirectories so it only rsyncs the files within a directory? I know of the --exclude command, but surely one mustn't have to type --exclude followed by every subdirectory individually ?? ie., I have "stuff" dir with 5 subdirs and 10 .txt files, I only want to rsync the 10 .txt files, leaving out the subdirs.


I have made a little script right now and then will add a cronjob to automate this weekly. Man this rocks :D

---

### Post by herbster on 2007-06-29
Okay someone wanna help with the cronjob? :D

Tried:

```
0 03 * * * sh /home/bobby/scripts/rsyncbackupscript
```

Didn't work, so I did:

```
0 03 * * * export DISPLAY=:0 && sh /home/bobby/scripts/rsyncbackupscript
```

Which popped up a dialog box asking me for my passphrase, which I entered, and then nothing, so I did

```
0 03 * * * export DISPLAY=:0 && gnome-terminal --command sh /home/bobby/scripts/rsyncbackupscript
```

Which did nothing. Argh! Can someone help me get this to go.

(And yes I changed the times to now for testing, that's just my target time)

I have also done chmod a+x for the script, it works on its own just fine.

---

### Post by qpieus on 2007-06-29
> **herbster said:**
> 
I am still wondering though, how do I exclude subdirectories so it only rsyncs the files within a directory? I know of the --exclude command, but surely one mustn't have to type --exclude followed by every subdirectory individually ?? ie., I have "stuff" dir with 5 subdirs and 10 .txt files, I only want to rsync the 10 .txt files, leaving out the subdirs.


I have made a little script right now and then will add a cronjob to automate this weekly. Man this rocks :D
you can use```
--exclude-from=FILE
``` instead of --exclude=   a bunch of times. FILE is simply a text file with a list of the subdirs you want to exclude, one subdir on each line of the text file. Make sure to include the actual path to the FILE so rsync can find it. This definitely simplifies your rsync command by getting rid of multiple --excludes.

---

### Post by qpieus on 2007-06-29
Regarding your script you want to run with cron. Are you backing up locally or is it to the remote server you talked about earlier? If you are rsyncing to a remote location, the cron job is probably getting stopped because the remote server wants you to log in. If that's the case, you can use ssh and rsync in the same command to connect and then backup files. You'll need to set up ssh keys on each machine so the script will work without having to login with a password.

For example:

rsync -e ssh -avz --delete /mydir/to_backup_up/ [email]user@myhost.com[/email]:/mydir/backup/ >> ~/backup.log

There's tons of examples on the net. Here's a couple:

[http://uberthings.com/2006/06/27/free-remote-backup-passwordless-ssh-rsync/](http://uberthings.com/2006/06/27/free-remote-backup-passwordless-ssh-rsync/)

[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

---

### Post by herbster on 2007-06-29
qpieus,

Okay, I'm getting a bit confused now. I followed this: [http://www.suso.org/docs/shell/ssh.sdf](http://www.suso.org/docs/shell/ssh.sdf)   and set up ssh, and I set up my keys and my passphrase. I just did this:

```
rsync -e ssh -avz --delete /media/stuff user@website.com:backup/ >> ~/backup.log
```

in terminal, and it asked me for my passphrase, then my login password and then it worked. I think I am at the point where I need to have it stop asking me for my passphrase and password.

I have checked both links you gave and with the first one, the cmd

```
sh user@thehost.com &#8216;test -d .ssh || mkdir -m 0700 .ssh ; cat >> .ssh/authorized_keys && chmod 0600 .ssh/*&#8217; < ~/.ssh/id_dsa.pub
```

It said "command test not found" and wouldn't go. The second link I am confused by to be honest, because I did that second step of "ssh-keygen -t dsa" accordance with the first link I pasted above, the HowTo I used.

So I'm sure it's a matter of proceeding from the point of setting it up so that my passphrase and password are "stored."


EDIT:

Okay, I used ssh-agent by having done
```
ssh-add
```
and I rsync'd a bunch of times and it didn't ask me to reenter my passphrase/password, so that seemed taken care of.

However, the cronjob is still asking me. I edited the cronjob to open gnome-terminal and run the command, and it asked me for my passphrase. Grrrr :mad:

---

### Post by qpieus on 2007-06-29
Ok, so one issue is that when you set up your ssh keys you used a passphrase. That's why your backup script is failing when run by cron, because it needs you to enter the passphrase. When I set up my ssh keys, I just hit the carriage return when it asked for a passphrase. This way there is no passphrase and then ssh+keys allow me to connect to a remote computer without actually having to enter my username and password. The page you linked to, near the end, talks about ssh-agent which can apparently handle your passphrase automatically so you don't need to enter it everytime. I have no experience with ssh-agent though.

If you want to try the no passphrase thing you can just rename your old keys and make new ones without a passphrase. Keys are stored in /home/username/.ssh and are called id_dsa and id_dsa.pub. Then copy your public key onto the remote machine into the authorized keys file, just as you did before. We know you already had this working, so set it up just like you did before, but with no passphrase on the keys.

Once this is all set up you should be able to ssh into the remote machine and it will automagically log you in. Once you verify that works, then your script should work because it won't be waiting on you to enter the passphrase.

---

### Post by herbster on 2007-06-29
It was the doggone passphrase! I just tested it and it's working perfectly :)

Thanks SO much for your help qpieus, this was very important for me to get working and I'm so glad it does. A couple rather minor things now:

1. I use:
```
export DISPLAY=:0 && gnome-terminal --command='rsync -avz --progress --delete -e ssh /media/extra/ubuntu-customizing/icons/ bobgilln@bobgill.net:backup'
```
which pops up a terminal and shows the output, but the terminal closes right away when the rsync is done. If I set this cron to run at like 4am, I'd like the terminal window to stay open, how could I do that? I tried adding a "&" at the end but it didn't work.

2. If I don't use a terminal-window, the command will run but I can't see it? Is there another way?

I know of the ability to output to a log file, but I'm not sure which is the more efficient option.

---

### Post by qpieus on 2007-06-30
I'm glad to help. I've learned a lot from these forums, so I'm happy to be able to help someone else.
Regarding the output from your cron job, I don't think either of your choices is more efficient, just choose which one you like best. I prefer outputting to a log file, so I can check it out later. Regarding trying to keep the gnome-terminal window open - I use KDE and it's terminal program (konsole) has a --noclose option. Looking at the man page for gnome-terminal, I see a couple options that might do the trick for you:
```
--window-with-profile=PROFILENAME
    Open a new window containing a tab with the given profile. More than one of these options can be provided.
```
```
--geometry=GEOMETRY
    X geometry specification (see "X" man page), can be specified once per window to be opened.
```

Type man gnome-terminal to see more.  I have not used gnome-terminal before , so I can't offer any help other than trying out the different options. Hey, you could always install KDE and use konsole :)

Edit:

I just did a search on the forums and came across this thread asking exactly what you want to do:

[http://ubuntuforums.org/showthread.php?t=326031](http://ubuntuforums.org/showthread.php?t=326031)

I can't tell from the responses but I get the idea that you might not be able to get gnome-terminal to stay open like you want. One of the responses talks about 

gnome-terminal --window-with-profile=xxxxx

but I can't tell if that worked or not.

---

### Post by herbster on 2007-06-30
qpieus,

Freakin' great, friend! I got it to work just fine. I made a new gnome-terminal profile called Stays (clever huh? :D) and the cronjob I used:

```
export DISPLAY=:0 && gnome-terminal --window-with-profile=Stays --command='rsync -avz --progress --delete -e ssh /media/extra/ubuntu-customizing/icons bobgilln@bobgill.net:backup/feisty-system'
```

Now I'm going to put that into a script and boom :D

Learning to use rsync and ssh even at this beginning level is just amazing, such simple tools that are so powerful and efficient.

BTW, I notice the -a and -z aspects of the rsync command, which are archive and compress. What is the compression implying? In rsync --help it just says "compress the data of the file transfer," but is it that the files are compressed, then uploaded to my server, and uncompressed all very quickly file by file? That the type of transfer is compressed in some other sense?

And what does it mean to archive? Again, --help only said "archive mode."

---

### Post by qpieus on 2007-06-30
Congrats on getting it working. That's a good feeling, isn't it. I would have never thought of profile=stays.

Try "man rsync" in a terminal, instead of rsync --help. man rsync calls up the so-called man pages, which have detailed info about the command. You can use man ...   with just about any command to see that command's man page.

From the rsync man page:

The -a (archive) option is equivalent to all of the following options
```
-a, --archive               archive mode, equivalent to -rlptgoD
```
So, this one letter does the same job as all those other ones (you can look them up in the man page). The important part of -a for me is that it works recursively through my directories.

For -z compression, here's what the man page says
```
-z, --compress
              With  this option, rsync compresses any data from the files that
              it sends to the destination machine.  This option is  useful  on
              slow  connections.   The  compression  method  used  is the same
              method that gzip uses.

              Note this this  option  typically  achieves  better  compression
              ratios that can be achieved by using a compressing remote shell,
              or a  compressing  transport,  as  it  takes  advantage  of  the
              implicit information sent for matching data blocks.
```
Some other info I found on the web says rsync compresses the data on the fly as it's transferring.

---

### Post by herbster on 2007-06-30
qpieus,

Okay, the -z makes sense now, but as for -a/archiving, I don't understand what it's "preserving" (from the man page). The permissions of the files?

And I just submitted a HowTo based on this thread that hopefully is approved in the Tutorials and Tips forum.

---

### Post by qpieus on 2007-07-02
```
-r recourses into subdirectories
-l copies symlinks as symlinks  (not sure what that means)
-p preserves file permissions
-t preserve times
-g preserve group
-o preserve owner
-D preserve devices (root only)

```

It looks like it will preserve just about everything with the file - permissions, owner, times, etc. I take that to mean it will not change the owner to you, for example, if you are the one doing the rsync. So if there is a file being rsync'd that is not owner by you, the copied file will not be owned by you either, it will retain all of it's original attributes.

---

