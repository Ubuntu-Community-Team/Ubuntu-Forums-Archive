---
title: "The Umpteenth Gutsy/Leopard networking thread"
date: 2008-04-20
forum: General Help
---

### Post by SodbusterXIV on 2008-04-20
I'm trying to share files between my desktop ("Ubie") which runs Ubuntu Gutsy and my white macbook ("Mactheknife"), which is running Leopard. I'm sharing from my desktop using samba, and it works beautifully.; I can see Ubie from Mactheknife, When I click on Ubie, I can click "connect" and then it connects me after I enter a password. I set mactheknife to share files using smb using Leopards built in GUI (sharing > file sharing>options>smb) As long as my macbook isn't sleeping, Ubie can see Mactheknife, but when I click on the icon I get the error message "Sorry, couldn't access all the files..."
When I type "smbclient -L //mactheknife" in terminal I get the error message "NT_STATUS_ERROR_BAD_NETWORK_NAME". Mactheknife is password protected (let's say, "user", "alohamora")

I am not wedded to using smb, of course. I tried using afp. Under "file sharing" on Mactheknife" I set it to share using appletalk, and installed the appropriate afp client programs on my Ubie. I was able to connect to mactheknife on my desktop just fine using terminal. Here my problem is that I'm not sure exactly how to edit "/etc/fstab". I tried following Alex "the Puffin" deVries's instructions to know avail. 

I think my main problem is that I have a very poor understanding of the file systems on both computers.  The instructions on how to use any sort of file sharing servers and clients are vague because they tend not to provide concrete examples illustrating what a "share" is, what a "host" is, etc. Furthermore, a lot of the forums have gotten spammed pretty heavily, making "googling" my problem a titanic waste of time. Since I'm an impoverished, and extremely busy, grad student, I can't afford to do that. So I decided to post here.

Please forgive my rambling, I'm very new at this. I'll provide whatever specs I can.

---

### Post by SpaceTeddy on 2008-04-20
mhm... if you just want it simple and fast, i would suggest you use the ssh-server. Install it on both computers, and you can pretty much instaltly use it in linux. to access the ubuntu by just typing ssh://ip of your macbook. 

the other way around i don't know how it works, as i am not a big fan of mac's and have never touched one. however, i have seen it done. 
so, all i can tell you is the idea, not the specs on how to set it up... sorry. Also, i have NO IDEA on how to get an ssh server running on a mac. sorry...

---

### Post by SodbusterXIV on 2008-04-21
Update: I managed to set Mactheknife up as a nfs server by creating and editing /etc/exports, then restarting nfsd. Then I edited /etc/fstab on Ubie and rebooted. That did the trick. I can mount my /Users directory on to Ubie. My home folder is locked on Ubie, but I really don't mind that; I can use the meta-user "Shared" as a drop box.

---

### Post by SodbusterXIV on 2008-04-22
Further update:

On the mac, I created a "sharing only" account named "Ubie". I used advanced preferences to give "Ubie" the same UID that I have on the desktop machine. Then I granted my dummy user full access to all the files in my home folder (there's a trick to doing that! Get info on home folder, then control click, then "apply to files and subfolders" or something like that). Then when I connect to my macbook from my desktop, I have full access to my home folder.

---

### Post by DBrocks on 2008-04-22
Would you please mark this thread as solved. It helps out people trying to find an answer to their questions, and it helps us as the people who try to solve other's problems. 

Thanks!

---

### Post by SodbusterXIV on 2008-04-24
ACK!!! Desperate need of serious Unix geek. Permissions between the two machines are snafu'd again. Any ideas?

So much for marking the problem as solved.

---

### Post by SpaceTeddy on 2008-04-25
without and detail... no - i don't have any ideas. What did you do, how did you get it to work, and what is error now ?

can you please provide some details ?
thanks

---

### Post by SodbusterXIV on 2008-04-25
Well--I think I fixed it. My /etc/exports file on the mac was incorrect.
If my Rube Goldberg home network is still functioning in a week I will post my method--until then I won't pollute cyberspace with misinformation. Wish me luck!

---

