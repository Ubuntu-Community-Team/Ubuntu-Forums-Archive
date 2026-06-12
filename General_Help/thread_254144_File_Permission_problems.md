---
title: "File Permission problems"
date: 2006-09-09
forum: General Help
---

### Post by Carol1976 on 2006-09-09
I converted from Windows XP a good few months back, and kept quite a few of my folders that I wanted when I installed Ubuntu.

I have Ubuntu installed on my 20Gig drive, and my /home directory is on my 200Gig Drive (not recognised as full 200Gig as I've not formatted it since I had my new mobo that supports it)

These folders that I kept have been marked as owned by root, including every single file inside these folders.  This wasn't a problem - or at least it didn't seem to be on the first install.

I then decided to try Kubuntu, so I installed it so I could dual boot with Ubuntu.. Kubuntu caused me great problems - I had a constant battle with the Klauncher and Dcop server breaking, so I was unable to perform ANY action as root (kdesu konqueror, or kdesu kate for instance)..

After NUMEROUS re-installs (one of them included moving all my folders from Home into a newly created partition so that I could format the /home directory so it became a completely fresh install, I then moved the folders one by one back onto the /home directory), I still had problems so after lots of shouting and wanting to throw my pc out of the window, I came back to Ubuntu (I still miss the "themeability" of Kubuntu, but I guess I can live without it as long as I have a working system)

My problem now is that these folders are all marked as belonging to root.  It's not a simple case of doing a chown option (like Simon tried to find out for me earlier) as my 7GIg of music was created in windows, so the filenames cause problems when I try to change their folder names (because they have characters and ampersands and spaces etc etc in them).

So.. other than going into each and every file of the 7Gig of music I have stored and removing characters and spaces... is there another way I could do this?

I thought of moving my entire /home folders over to the 40Gig partition I made, and then creating NEW folders on /home with carol as the owner, and then copying the individual files over, but I'm guessing that they will keep their root ownership, even though I am writing them back to home?

I tried changing the ownership of one of the folders via sudo nautilus, and it just changed the ownership of the folder and not the contents.

From what I can make out as a relative newbie to this I have two options:

1. rename each and every file so that they are compatible with "linux files" (ie no characters and no spaces) so that I can then batch ownership change them.

2. change the ownership of each and every file, thus not having to change the names of these files?

The reason I am asking is because in their current state, NONE of my media players will play them, I can only play them if they belong to me. :(

Please assist?

---

### Post by kidders on 2006-09-09
Hi there,

I think you have things a bit backways ... To my knowledge, it's Windows (and not Linux) that is fussy about what you're allowed to call your files. Linux will let you use any combination of characters you wish in filenames. If you wanted to call something "!%^::::    ***?", Ubuntu will happily let you.

Anyhow, I'm presuming that the partition you're having trouble with uses a Microsoft filesystem, in which case the permissions attached to the files are completely arbitrary, as they don't really exist. Accordingly, Linux will invent strict ones, just to play it safe.

Say your partition is mounted at /mnt/windoze. Normally, **chown -R username /mnt/windoze && chmod -R u+w /mnt/windoze** will change the owner of *everything* in it to "username", and grant him write permission. Since, in this case, the ownership/permissions are most likely "invented", you have to set them when you mount the partition in the first place.

Take a look at the man page for **mount** ... you will see options such as **umask**, **gid** and **uid** that allow you to override default permissions with new ones, for an entire partition.

---

### Post by Carol1976 on 2006-09-09
hmm okies, I did a chown -r /carol/home/music and all the files that had either spaces in their file names or the & character got refused and it said it was because it didn't allow " " character or & (ampersand).

I will get Simon to help me understand what you mean in your last sentence rofl ;)

---

### Post by kidders on 2006-09-09
Hehe... I just wanted to save myself re-typing something VERY long-winded that is in the manual page for "mount" anyhow :-P

I've never seen that error message you mentioned before. How very strange! What filesystem are you using? (You seem to have undergone a few changes!)

---

### Post by Carol1976 on 2006-09-09
It is an EXT3 partition not a windows partition, so is there something else that I should be doing other than what you said (as you seem to have presumed it was windows)

Thanks for the help so far ;)

---

### Post by kidders on 2006-09-09
Yeah, I did :-( The sort of problem you're describing is unheard of with ext3 in my experience, you see. To my knowledge ext3 even allows '/' in its filenames, which would be the equivalent of Windows letting you call a file "C:\".

I may be missing something in your posts, but it seems to me that if certain characters weren't allowed in filenames, you couldn't have gotten them onto the disk in the first place.

Any chance you could post the exact text of the error messages you see? I'm quite interested to find out what the problem might be!

---

### Post by Carol1976 on 2006-09-09
> chown: changing ownership of `/home/carol/MUSIC/Vangelis/Jon & Vangelis - I\'ll Find My Way Home.mp3': Operation not permitted (you'll notice that a \ has appeared that wasn't previously in the filename)

I haven't had the error about the " " and & again... I'm confused now as to how I actually got that message rofl

*tries again*

nope I can't get that error message to come up again 

](*,)

---

### Post by kidders on 2006-09-09
All that message means is that the user executing the "chown" doesn't have the authority to change the ownership of the file.

You can't just swipe a file off the superuser! You have to **be** the superuser to do that!

Incidentally, the addition of backslashes like you pointed out is a security feature, designed to prevent users on big Linux systems deliberately naming their files things that might cause a program using the output of a "chown" command to behave unpredictably or do bad things by accident. It's called **escaping**.

In addition, you'll notice that, to successfully execute a command called "hello world", in bash, you'd have to put quotes around its name. Escaping it as **hello\ world** removes the need to do that.

---

### Post by Carol1976 on 2006-09-09
so, how would I get in as superuser to then give all the files to the "user"

Incidentally, I have just sat and opened all the folders so that every file is listed in a sudo nautilus window and selected them all and given "others" the permisson to "read, write and execute" them, otherwise my 7gig of music would be completely useless, as NONE of my music players wanted to play them.

*sighs* I now have to do that with EVERY file that was put back on the harddrive after install - I think about 20gig of stuff in total :(

---

### Post by kidders on 2006-09-09
"chmod 777" is not a smart move ... it would allow both malicious and accidental deletion of your files. Permissions changes for several gigabytes of files should only take a moment or two (as would deleting them!), so there's no problem there.

It sounds as if you could do with reading a little about Linux's security model ... Google can help with that. In the meantime, suffice it to say that you can't access something you don't have permission to, nor can you grant yourself permission to access something you don't have permission to, which is quite sensible.

To transfer ownership of something away from the superuser, either sudo your chown command or log into a terminal as root and do it that way. Whichever you choose, I'd be quite suprised if "chown -R carol:carol /home/carol/MUSIC" took very long. I'd also reccommend a "chmod -R 640 /home/carol/MUSIC", to set the file access permissions to something reasonable, and a "chmod -R +X /home/carol/MUSIC" to ensure directory permissions are as expected.

---

### Post by CatKiller on 2006-09-09
> **kidders said:**
> ...either sudo your chown command ...
Crikey. I already know what you're saying and I find that confusing. What this means is that if you wanted to run a command as the superuser, say, ```
chown -R carol:carol /home/carol/MUSIC
``` you would instead enter ```
sudo chown -R carol:carol /home/carol/MUSIC
``` It will then ask you for a password. If you are logged in with the first account you created during install, this will be your user password.

---

### Post by kidders on 2006-09-09
I guess so :-)

There's nothing particularly scary about sudo ... it's just a tool designed to let you give people permission to do certain things as though they were root, without giving them free reign. Handy!

The basic principle behind my last suggestion is to make sure you own the files you are referring to ... if you don't there's no reason to expect that you would be allowed to access them.

---

### Post by Carol1976 on 2006-09-10
lol thanks peeps, I actually decided to "guess" and put sudo in front and I managed to get it all changed to carol (being my username) without a hitch.

I tried to modify my post last night to say, don't worry sussed it, but the forum wouldn't let me. (was running exceptionally slow)

---

