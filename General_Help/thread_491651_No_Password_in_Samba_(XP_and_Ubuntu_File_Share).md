---
title: "No Password in Samba (XP and Ubuntu File Share)"
date: 2007-07-03
forum: General Help
---

### Post by AhrenBa on 2007-07-03
Hello,

I followed this video to setup file sharing between my Windows XP and Ubuntu machines. ([http://youtube.com/watch?v=Ad17kma8rNM](http://youtube.com/watch?v=Ad17kma8rNM)).

I got to the point where both computer can see each other and are in the same workgroup. Each computer has at least one shared folder.

**I have two things I need help with:**
1. When I try to access the **Windows shares from the Ubuntu computer**, it prompts me for authentication (username and password). However, I do not have a password for the windows machine, so I have no clue what to use here. Why is it asking for a password here? How can I either turn this off or find out what it wants? Because of this, I cannot access my Windows shares from the Ubuntu computer.

2.  When I try to access the **Ubuntu shares from my XP computer**, it requires me to input the password I setup when I added a user to Samba. It works when I input the password, but this is sort of a hassle. Is there a way to turn this off? I can access the Ubuntu shares from this (XP) computer.

Thanks!
[B][B]
EDIT/UPDATE:[/B]Ok, I just had a "major breakthrough". I just tried sharing some other folders on my XP machine, and then tried accessing them from Ubuntu, and those ones worked! I didn't do anything different in the process.

However that other folder still doesn't let me access it without a password etc. Does this explain anything? I don't get why it's doing this.[/B]

---

### Post by Jem00 on 2007-07-03
try this page
[URL="http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/"]
http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/[/URL]

---

### Post by AhrenBa on 2007-07-03
> **Jem00 said:**
> try this page
[URL="http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/"]
http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/[/URL]

Thanks for the response, but I have actually been able to get to this point. I have gotten to  having both computers see each other, but am having problems with the passwords.

Anyone else have any ideas?

---

### Post by Das Oracle on 2007-07-04
I am having the same issues, and if anyone could help you would be helping two people out now:

specifically connecting to ubuntu via xp it asks for username/pass, I input those and then it re-opens the window (as if authenication failed) and puts username as current xp box name / username

---

### Post by AhrenBa on 2007-07-04
> **Das Oracle said:**
> I am having the same issues, and if anyone could help you would be helping two people out now

So, let's see. You don't have a password on your XP machine, correct? And you can access Ubuntu shares from XP, but not XP shares from Ubuntu since it requires a login that we do not know? Is this correct?

---

### Post by Das Oracle on 2007-07-04
xp machine was actually a friends, and i could access it ok. My issue with that was I could not see it at first. Having changed to the same group as him everything was ok. Getting from him to my shares had the same issue you are having. It asks for user/pass i enter said info and it keeps re-prompting me for the info.

---

### Post by AhrenBa on 2007-07-04
> **Das Oracle said:**
> xp machine was actually a friends, and i could access it ok. My issue with that was I could not see it at first. Having changed to the same group as him everything was ok. Getting from him to my shares had the same issue you are having. It asks for user/pass i enter said info and it keeps re-prompting me for the info.

Ok, that's good. We are on the same page. So you can access Ubuntu from XP just fine correct?

I have seriously looked all over the web for a solution and cannot find one. I will definitely let you know if I find one, and I hope you will do the same. Let's just hope someone replies here.

---

### Post by Das Oracle on 2007-07-04
negative, otherway around. I can access xp from ubuntu fine, but not ubuntu from xp

**edit** have you tried looking at solutions regarding smb.conf?

---

### Post by AhrenBa on 2007-07-04
> **Das Oracle said:**
> negative, otherway around. I can access xp from ubuntu fine, but not ubuntu from xp

**edit** have you tried looking at solutions regarding smb.conf?

Yes, but I am not sure if I am doing the right ones. The thing that baffles me is that I have no password setup for any of my accounts on the XP machine, but yet Ubuntu still wants me to put in a username/password before I can access the XP's shares.

Do you have any ideas?

---

### Post by Das Oracle on 2007-07-04
do you have the permissions on file sharing set up properly in xp? I recall having a similar problem back with edgy and the reason was with security permissions on the xp machine for shares. I don't remember clearly but I think that is what my problem was.

---

### Post by AhrenBa on 2007-07-04
> **Das Oracle said:**
> do you have the permissions on file sharing set up properly in xp? I recall having a similar problem back with edgy and the reason was with security permissions on the xp machine for shares. I don't remember clearly but I think that is what my problem was.

Hmmm... I don't recall changing anything, but where would I change these permissions?

---

### Post by Das Oracle on 2007-07-04
right click on your share folder and check there. If all else fails here is a link to the MS site

[http://support.microsoft.com/kb/304040]("http://support.microsoft.com/kb/304040")

---

### Post by Nythain on 2007-07-04
has anyone mentioned changing security=user to security=share in the /etc/samba/smb.conf yet... should make it so you dont need a password to access the ubuntu share from an xp machine

---

### Post by AhrenBa on 2007-07-04
> **Nythain said:**
> has anyone mentioned changing security=user to security=share in the /etc/samba/smb.conf yet... should make it so you dont need a password to access the ubuntu share from an xp machine


Yes, I believe this has solved my problem for the "going from XP to Ubuntu". I am no longer prompted for a password when I go this way.

However, when I go from Ubuntu to XP, this is where the problem lies. It prompts me for a username, domain, and password. I have no password setup on the XP machine, so I have no clue what it is using. No matter what I enter, it just pops back up again, asking the same thing.

---

### Post by AhrenBa on 2007-07-04
Ok, I just had a "major breakthough". I just tried sharing some other folders on my XP machine, and then tried accessing them from Ubuntu, and those ones worked! I didn't do anything different in the process.

However that other folder still doesn't let me access it without a password etc. Does this explain anything? I don't get why it's doing this.

---

### Post by Nythain on 2007-07-04
that pesky folder wouldnt happen to be a root folder, like all of c:\ or anything would it???

---

### Post by AhrenBa on 2007-07-04
> **Nythain said:**
> that pesky folder wouldnt happen to be a root folder, like all of c:\ or anything would it???

Nope, it is just one of the folders on the desktop. However, I did notice something strange.

When you check the box (in windows) to allow this folder to be shared, it'll say "setting folder permissions" for a few seconds. For the folders it does that, those work. Then, when I share some folders (including the one that is not working), it doesn't do this "setting folder permissions".

---

### Post by Nythain on 2007-07-04
is it a problem with any folder on the desktop or just that one folder on the desktop... and is that folder just a link to somewhere else like my documents or whatnot... im shootin in the dark here, i havent messed with windows in forever and a day

---

### Post by xiutech on 2007-07-16
> **Nythain said:**
> has anyone mentioned changing security=user to security=share in the /etc/samba/smb.conf yet... should make it so you dont need a password to access the ubuntu share from an xp machine

I was having this same problem and using *security = share* worked for me: after making this change, my Windows XP machine got access to all the shared files on my Ubuntu machine. Thanks!

Is there a Samba / Windows / Ubuntu bugfix or configuration option that would allow Windows to access Ubuntu server files when *security = user* is  turned on? 

Access from Ubuntu to the Windows machine, and from one Ubuntu machine to another, has worked fine.

---

### Post by xiutech on 2007-07-17
I subsequently realized I had forgotten to create a SAMBA account on the Ubuntu box that I was trying to access. I had a Ubuntu/Linux user account there, but had not created an additional SAMBA user account. 

So I reset the configuration to security = user, set the file sharing permissions, and I was able to access those files (make edits etc.) with security enabled.

There is an [excellent video posted on YouTube by PCMechTV.com]("http://www.youtube.com/watch?v=Ad17kma8rNM&mode=related&search=") which clearly explains how to do this.

---

### Post by Varadin on 2007-12-09
I was of the understanding that samba would use your passwd file from the linux box.  At least that's the way that the samba.conf appears...

My XP box was prompting for a password to access \\varadin-desktop or any of the shares under it, for example \\varadin-desktop\music or \\varadin-desktop\public

What I did, and I don't know if it's correct - was 

```
sudo smbpasswd -a varadin
```

Where "varadin" is your own username.

It then prompted me for a password twice, and then I was able to log in using the username and password I had just set to all my shares.

Wish I had more information about this, but it works for my purpose... hope this helps.

---

### Post by osx on 2007-12-24
Here is what I did that made it get passed the password issue.

1. Go to [http://screencasts.ubuntu.com/SAMBA_Filesharing](http://screencasts.ubuntu.com/SAMBA_Filesharing) and watch the screencast on setting up file sharing through SAMBA. This alone will not make it work.

2. Follow the instructions given by "Submitted by Anonymous on Sun, 2007-10-21 17:08." on the above screencast link for setting a Samba password. This information is in the very first comment.

3. Finally, scroll back up the page (i.e., at the above link) and find additional notes left by the author of the above screencast. Follow those instructions which are

"Notes Andrew adds: "You may have problems accessing your share from other computers afterwards. To fix this issue do the following things. Launch the run dialog by pressing Alt+F2. Enter the command gksudo gedit /etc/samba/smb.conf then enter your password when prompted. Find the security section of the configuration file. Change "user" to "share" and remove the semicolon from the start of the line. Find the guest account section. Change "nobody" to your account's username and remove the semi colon from the start of the line. Save the file and restart your computer"

After this third step, I was able to log into my Ubuntu share from Windows without problems.

---

