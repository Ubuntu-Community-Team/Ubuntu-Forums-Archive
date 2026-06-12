---
title: "Nautilus MASSIVE security fail?"
date: 2012-12-24
forum: General Help
---

### Post by jhwoods on 2012-12-24
Doesn't anybody else think it is a MASSIVE security fail that Nautilus quietly thumbnails all opened files in a single place?   I can plug in a USB, or mount an encrypted volume, read some documents and Nautilus will put readable thumbnails into my (unencrypted) home directory.  

My current workarounds
- turning off thumbnailing -- but I don't really want to
- removing .thumbnails and replacing with symlink to /dev/shm
  -- this causes the 'normal', 'fail' and 'large' subfolders to get created on the RAM disk

I think it would be preferable to create a .thumbnails in each directory.  Surely this would be faster, easy to manage size-wise, and -- most importantly -- it would ensure that the thumbnails enjoyed the same security status as the files from which they are derived.

---

### Post by rnerwein on 2012-12-24
> **jhwoods said:**
> Doesn't anybody else think it is a MASSIVE security fail that Nautilus quietly thumbnails all opened files in a single place?   I can plug in a USB, or mount an encrypted volume, read some documents and Nautilus will put readable thumbnails into my (unencrypted) home directory.  

My current workarounds
- turning off thumbnailing -- but I don't really want to
- removing .thumbnails and replacing with symlink to /dev/shm
  -- this causes the 'normal', 'fail' and 'large' subfolders to get created on the RAM disk

I think it would be preferable to create a .thumbnails in each directory.  Surely this would be faster, easy to manage size-wise, and -- most importantly -- it would ensure that the thumbnails enjoyed the same security status as the files from which they are derived.
hi
when you can plug in a USB you have phisical access to the box. it's christmas just take the whole box. :p
cheers

---

### Post by 3rdalbum on 2012-12-24
I don't think it's a "massive" security failure. I can't think of a hypothetical situation where any harm could be caused. Can you let me know one? Let the Ubuntu mailing list know?

---

### Post by iponeverything on 2012-12-24
are you kidding, this is BIGGER than the sendmail hole of '94..

- If you have encrypted thumb drive and it is lost, you are good, the files are encrypted.

- If you have encrypted thumb drive and you use it in untrusted computer, the "fail" is yours.

- If you don't trust your own computer, and you don't do anything about it like encrypting your home or the whole drive, then you use the encrypted thumb drive in it  -  the "fail" is yours.

---

### Post by SeanBlader on 2012-12-24
I guess the level of this security hole then has more to do with how secure you think your home folder is. I for one find it to be more secure than you find yours, and mine is unencrypted as well.

Moral of the story is, don't go losing your computer.

---

### Post by jhwoods on 2012-12-24
Guys, thanks for your input.

@rnerwein - I can't agree.  If I have a volume on my disk that is suitably encrypted, it doesn't matter if you have physical access to the box, my stuff is still protected - I've lost it, but you can't see it.

@3rdalbum - How about this: I have a secret project.  I keep the files on an encrypted thumbdrive, along with portable Truecrypt.  I stick it in my laptop, mount the volume, and work on the files.  Later there are thumbnails that are visible in my home directory on the laptop.  These are at a lower level of security than my thumbdrive, both because I could put the thumbdrive in the safe and because I'm almost certainly using a shorter password for my Ubuntu logon than my Truecrypt volume.  If thumbnails for the TC volume were kept on that volume, they would be at the same level of security as the TC volume itself, which seems to me to be appropriate.

@iponeverything - as in the scenario above, I like to have levels of encryption.  My home folder might have one level of encryption and a Truecrypt volume might be higher.  If I mount a TC volume of porn videos, or secret documents, I don't want the thumbnails to be stored at the lower level of security when I have dismounted the TC volume.

@SeanBlader - I'm not quite sure why you find your home folder to me more secure than mine; I don't use full disk encryption but my home dir is encrypted.

@all - I still don't see the case for having all the thumbnails in one place in the home dir.   At best it's not better than having separate dirs (like the Windows thumbs.dir used to be, although bizarrely Microsoft appear to use a central directory now), and at worst it results in exposing some of the contents of files that a user might be forgiven for thinking were more secure.

---

### Post by mc4man on 2012-12-24
> **jhwoods said:**
> Doesn't anybody else think it is a MASSIVE security fail that Nautilus quietly thumbnails all opened files in a single place?   I can plug in a USB, or mount an encrypted volume, read some documents and Nautilus will put readable thumbnails into my (unencrypted) home directory.  

 
Can't say that any of my 'secret' text or code files are ever thumbnailed & even if they were doubt much could be 'easily' read.
Can you attach such an example?

---

### Post by snowpine on 2012-12-24
Edit->Preferences->Preview->Show Thumbnails->Never

---

### Post by jhwoods on 2012-12-24
@mc4man - Here are two examples.  One of these thumbnails gives away the content of my project, and the other shows a blonde woman with my horse.  Fortunately the project is fictitious, and the blonde is my wife.  

Text files are worse - on my desktop, icons for text files give away the first 4-5 chars of the first 4 lines - that's enough to make bank details or passwords a lot less secure.

@snowpine - I pointed out in my first post that you could turn it off.    My own workaround is, in my opinion, even better - write the thumbnails to the ramdisk.  That way you can see them in use, but don't have to worry about them persisting on disk.

But my impression from the responses I have seen is that everyone is very keen to justify the status quo.   I'm a bit surprised no one has agreed with me, because my solution (write thumbnails in the appropriate directory) appears to be able to do everything that you guys want but your solution (leave it central and work round it) does not do everything that I want :-)

---

### Post by snowpine on 2012-12-24
> **jhwoods said:**
> I'm a bit surprised no one has agreed with me, 

Linux is "open source" so our emphasis as a community is not finding one single solution we can all agree on to make everyone happy as a group, but rather giving users the tools they need to become individually happy. :)

---

### Post by fdrake on 2012-12-24
> **jhwoods said:**
> Doesn't anybody else think it is a MASSIVE security fail that Nautilus quietly thumbnails all opened files in a single place?   I can plug in a USB, or mount an encrypted volume, read some documents and Nautilus will put readable thumbnails into my (unencrypted) home directory. may I remind you that in order to mount an encrypted usb drive you need to know the password. Now why would you mount your encrypted usb into a sys that you don not trust. You don't do it! The problem is not that the thumbs are saved. Who cares about it when the sys knows your pass, that's the last of your worries. 

YOU DO NOT MOUNT/OPEN ENCRYPTED DATA INTO AN UNTRUSTED SYSTEM. same concept goes for the webemail.

---

### Post by dcstar on 2012-12-24
> **jhwoods said:**
> 
............
I think it would be preferable to create a .thumbnails in each directory.  Surely this would be faster, easy to manage size-wise, and -- most importantly -- it would ensure that the thumbnails enjoyed the same security status as the files from which they are derived.

Then open a bug and mark it as a Security issue, that is EXACTLY why this process exists.

---

### Post by jhwoods on 2012-12-24
@snowpine - I understand what open source is.  It should be clear from my workaround, a symlink to /dev/shm, that I'm not exactly a unix noob, either.

I am quite aware that I can use another file-browser, another distro, or I could mod nautilus to behave in a different way.  None of that logically implies that I should overlook what seems to me to be a serious security flaw in a piece of software I have used.  

Can someone can give me a good reason for centralising thumbnail storage?  I am unconvinced that thumbnails from files on encrypted volumes should ever be stored elsewhere without the user deliberately choosing to make that  happen.

---

### Post by jhwoods on 2012-12-24
@fdrake I **do** trust my home system, in that I believe it is not currently compromised.  That doesn't stop me from believing my home-folder encryption to be weaker than that of my TrueCrypt volume, if for no other reason than password length (and there are other reasons).

The implication of your argument is that, if I choose to have my most sensitive work on a drive with a 40 character password, I should never mount it onto a system that has an 8 character password!  In fact, if your argument were to hold sway, nobody would use TC for anything other than full disk encryption.

---

### Post by jhwoods on 2012-12-24
@dcstar - thanks, I am strongly tempted to do so.  But I wanted to come to the forum first to see if I was missing something obvious.  I'm not currently convinced by any of the counter arguments presented to me and if that continues to be the case I most certainly will raise it as a security issue.

---

### Post by MG&amp;TL on 2012-12-24
> **jhwoods said:**
> 
Can someone can give me a good reason for centralising thumbnail storage?  I am unconvinced that thumbnails from files on encrypted volumes should ever be stored elsewhere without the user deliberately choosing to make that  happen.

Three reasons, as I see it:

1) It's more difficult to code for. If you've already got to figure out if you've got permissions on the drive to store thumbnails, whether the drive has the capacity or bandwidth required to store thumbnails (think floppy drives, one-write CDs, network shares), and whether the drive is nearly full or not, then thumbnailing is more of a headache.

2) It could slow down I/O traffic on old or network storage.

3) Dumping thumbnails in the directory they're in leaves rubbish all over the places you view in a file manager.

I can see where you're coming from, I was just thinking of reasons from a developer's point of view.

---

### Post by haqking on 2012-12-24
I wouldnt say it is a security issue, more of a privacy issue (though the 2 can be related depending on context).  Unless the readable thumbnails contain security related information such as passwords.

If someone other than you has access to the thumbnails then security has already been compromised and then in addition your privacy also.

Peace

---

### Post by snowpine on 2012-12-24
> **jhwoods said:**
> @snowpine - 

Can someone can give me a good reason for centralising thumbnail storage?  

Applications should only ever store data in your /home unless explicitly instructed otherwise, in my opinion. :)

---

### Post by SeanBlader on 2012-12-25
> **jhwoods said:**
> @SeanBlader - I'm not quite sure why you find your home folder to me more secure than mine; I don't use full disk encryption but my home dir is encrypted.


Because I have a more robust security mechanism for my computers, it's called a door lock. So if you don't have one of those and other people readily have access to your home folder then regardless of what kind of encryption you're running, with the cost and speed of data you can push through today's graphics chips, physical access to even encrypted data is nearly pointless.

And it sounds to me like if your home folder is encrypted with it's thumbnails, then it's just as secure as your encrypted USB key with the originals. So calling this a "MASSIVE security fail" seems a little sensationalist to me.

---

### Post by mc4man on 2012-12-25
Really don't see any issue here at all. If one has files they have concerns about then take care of them yourselves.
(- And currently nautilus (3.6+), stores the vast majority of thumbnails in ~/.cache/thumbnails. 

If one saves a text file & doesn't like what they see in the icon then they should also take care of it themselves, no big deal.

---

### Post by jhwoods on 2012-12-25
@MG&TL - that's the kind of answer I was looking for, I'll deal with that in a second.  Let me first deal with some of the people who ironically think I'm an idiot.

@haqking - you already agree with me that privacy and security are related, depending on context.  But again I dispute "someone other than you has access to the thumbnails then security has  already been compromised and then in addition your privacy also."  Different levels of encryption exist.  You might get my PC.  You might be able to decrypt my home folder relatively easily.  You still won't be able to decrypt my TrueCrypt volume - it has a higher level of encryption.  So why would I store the thumbnails from the that volume in my home dir - that is plain and simply a leak from a higher security level to a lower one.

@snowpine -  I agree, but caching thumbnails is a bit different from saving files.  If I load a document from secure storage, modify it and save it, where does it default the file save directory?  Does it save a copy in ~me?  I hope not!

@SeanBlader - my house is also locked.  The difference is, if someone breaks in, steals my computer, they cannot read my documents without a lot of effort.  More importantly, they cannot read the subset of those documents that I consider private without a ENORMOUS amount more effort - probably more than anyone apart from a government agency could bring to bear.  You have some idea how powerful GPUs are at encryption cracking, but you don't seem to recognise the massive difference in degree between hacking open a home folder protected by an 8 char password and hacking open a TC volume protected by a 40 char one.  I'm afraid the actual facts are against you on this one - it simply isn't the case that just because some encryption is easy to crack, that all of it is equally easy, which is the implication of your assertion.

Perhaps I annoyed people by calling this a 'massive' security fail, although at least I got your attention.  But really folks, in security circles, a mechanism that leaks some information from one security level to another, lower one is generally considered to have a problem.  I still have no reason to believe this is wrong.

What I do have, thanks to MG&TL, is finally an argument in favour of putting thumbnails in ~me that is more than "that's just the way we've always done it, deal with it"

>>1) It's more difficult to code for. If you've already got to figure out  if you've got permissions on the drive to store thumbnails, whether the  drive has the capacity or bandwidth required to store thumbnails (think  floppy drives, one-write CDs, network shares), and whether the drive is  nearly full or not, then thumbnailing is more of a headache.

Yes, I completely agree with that.

>>2) It could slow down I/O traffic on old or network storage.

Yes, it could, although can it work the other way around?  Having local thumbnails to old / network storage could slow you down, like the old windows explorer disappeared network share problem?  I'm not sure.

>>3) Dumping thumbnails in the directory they're in leaves rubbish all over the places you view in a file manager.

I'm less convinced about this, because you're going to get rubbish somewhere - either one copy on the network share, or every user has a copy, which is inherently more wasteful and less secure.

Ok, in the light of that, it seems to me that the problem is that Nautilus thumbnailing is not sufficiently granular.  How about it thumbnails everything that is mounted below /home/you in /home/you/.thumbnails but it only caches thumbnails from other mountpoints to RAM?

---

### Post by haqking on 2012-12-25
> **jhwoods said:**
> 

@haqking - you already agree with me that privacy and security are related, depending on context.  But again I dispute "someone other than you has access to the thumbnails then security has  already been compromised and then in addition your privacy also."  Different levels of encryption exist.  You might get my PC.  You might be able to decrypt my home folder relatively easily.  You still won't be able to decrypt my TrueCrypt volume - it has a higher level of encryption.  So why would I store the thumbnails from the that volume in my home dir - that is plain and simply a leak from a higher security level to a lower one.



Why dont you encrypt your home directory with truecrypt then ?

The thread title and content implies that this a major concern and that Ubuntu and Linux doesnt have any other security flaws, there are hundreds, alot of which can be addressed by the user, you have already encrypted using truecrypt to protect data, so use it to protect your home directory if your thumbnails are precious.

Peace

---

### Post by MG&amp;TL on 2012-12-25
> **jhwoods said:**
> 
>>3) Dumping thumbnails in the directory they're in leaves rubbish all over the places you view in a file manager.

I'm less convinced about this, because you're going to get rubbish somewhere - either one copy on the network share, or every user has a copy, which is inherently more wasteful and less secure.

Ok, in the light of that, it seems to me that the problem is that Nautilus thumbnailing is not sufficiently granular.  How about it thumbnails everything that is mounted below /home/you in /home/you/.thumbnails but it only caches thumbnails from other mountpoints to RAM?

Those are fair points you have. While I wouldn't say it was a security failure *per se*, it's certainly worth the developers having a think about. I guess you could raise a bug on the GNOME bugzilla. They could at least encrypt the thumbnail directory. :)

---

### Post by haqking on 2012-12-25
> **MG&TL said:**
> Those are fair points you have. While I wouldn't say it was a security failure *per se*, it's certainly worth the developers having a think about. I guess you could raise a bug on the GNOME bugzilla. They could at least encrypt the thumbnail directory. :)

Wont happen ;-)

---

### Post by MG&amp;TL on 2012-12-25
> **haqking said:**
> Wont happen ;-)

Nah, it won't. But it'll make OP feel better and keep the GNOME guys on their toes. ;)

---

### Post by iponeverything on 2012-12-27
The problem is your subject - it is a fail.

Folks read this post expecting a "MASSIVE security fail" and instead find nothing of sort - You might have been taken more seriously if you had used accurate subject. 

If this is a "MASSIVE security fail", I'd love see your subject line for a remote root exploit.

---

