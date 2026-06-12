---
title: "For some reason firefox can't save links or images. im using Kubuntu."
date: 2007-06-04
forum: General Help
---

### Post by reggierabbit on 2007-06-04
For some reason firefox can't save links or images. im using Kubuntu. But it works on windows xp. Im dual booting and im using the one profile.

---

### Post by x64Jimbo on 2007-06-04
What happens? Specifics are necessary.

---

### Post by zzarr on 2007-06-04
Same for me.

I can't save images ether.

I'm using ubuntu fiesty fawn (gnome).

What happens is there I right klick on the image I want to save and chose "save target as...", chose a location and "OK".

That's what happens and nothing more.

greetings zzarr

---

### Post by trak87 on 2007-06-04
> **zzarr said:**
> ..."save target as..."

You are saving a page, not an image. Choose, "Save Image As" instead.

---

### Post by zzarr on 2007-06-04
Yes

Of course... I wrote wrong, I'm from sweden and there for I says "save image as" in swedish, so I simply translated wrong.

But I chosed the correct alternative in any way.

greetings zzarr

---

### Post by trak87 on 2007-06-04
Make sure you are saving to an area where you have write permissions, like your /home/user area. Anything outside that and you probably won't be able to save anything.

---

### Post by zzarr on 2007-06-04
Yes, thanks.

I know that. :)

I'm not a beginner (I'm not upset, just telling).
I have administrated both linux and unix systems (like solaris) for 3 - 4 years now.

Just so you know what to excpect. :)

greetings zzarr

---

### Post by trak87 on 2007-06-04
Sorry for being so basic. It's hard to know how much experience people have. 

That's a strange problem and I'm afraid I don't have an answer for you.

---

### Post by trak87 on 2007-06-04
Wait. You say you are sharing a profile between two OS's? I think that's the problem. I've run into a similar problem I could never figure out using that technique. My problem was slightly different. I was moving Thunderbird email from Windows to Linux. For some reason the email data couldn't be read in the Linux version of Tbird. I checked permissions. I tried converting line feeds from DOS to Unix. I tried studying the email file in detail as it was just simple text. In the end I gave up as I never found a solution. But something there is obviously different.

You might try moving or renaming your .mozilla/firefox directory. Rerun Firefox (which will recreate the config files [I say this for the benefit of others, not you]) and see if the problem is solved.

---

### Post by reggierabbit on 2007-06-05
What happens is, i right click an image and i click save image as then nothing happens not even a location box thing.

---

### Post by reggierabbit on 2007-06-05
I think your right. I created another profile in the home directory and it worked fine. Can you give me instructions on what to do to fix ths. Im new to linux.

---

### Post by zzarr on 2007-06-05
Hello again!

I'm not sharing any profile, but it is an older profile from dapper.

So I guess I have to make a new one.

I'll tell the results later.

greetings zzarr

---

### Post by trak87 on 2007-06-05
> **reggierabbit said:**
> I think your right. I created another profile in the home directory and it worked fine. Can you give me instructions on what to do to fix ths. Im new to linux.

I don't know why the problem exists. There seems to be a difference between the Windows and Linux versions of Firefox and sharing a profile is problematic.

---

### Post by trak87 on 2007-06-05
Just thinking out loud here, but I wonder if character encoding differences between Win and Lin might be the problem...

---

### Post by x64Jimbo on 2007-06-06
I have also found profile sharing to be problematic and that it can lead to profile corruption, making it unusable in either OS. Much as it is a pain, you should probably keep separate profiles. One thing you might do is run firefox in Linux under Wine so that you're still using the windows version. I'm not sure how all that would pan out, but it is a possible solution to the differences there.

---

### Post by zzarr on 2007-06-06
Hi!

I haven't made a new profile yet.

In any way, I know there's drivers for linux filesystems for windows (such as ext2, ext3 and more).

So (I'm not using windows my self, so it's just a guess) I think it might be possible to have have to independent but identical firefox profiles by using symbolic links for the plugins/addons, favorites and so on.

greetings zzarr

---

