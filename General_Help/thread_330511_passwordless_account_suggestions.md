---
title: "passwordless account suggestions?"
date: 2007-01-03
forum: General Help
---

### Post by dannyboy79 on 2007-01-03
I run rkhunter and everyday I get this error:

Checking for passwordless user accounts... Warning!
-----------------------------------------------------------------

Found warnings:
[07:37:57] Warning! Found passwordless account (nobody)

-----------------------------------------------------------------

I am aware that this account is passwordless and really don't care. or should I? I only has guest account privalages so why should I care? WHat's the point of having a guest account if it has to have a password? for samba, some of my shares I allow guest access (no password entry) and with the smb.conf name mapping function you can map a network name to a computer name. for instance, I map the guest account within winxp to the nobody account on my machine so that they can at least read all the shares available. I don't allow nobody account ssh or ftp access so should this passwordless account really matter? I suppose someone could break into my machine using the nobody account and then try to brute force root's password but they would have to have physical access to my machine correct? Any help or suggestions would be appreciated.

---

### Post by dannyboy79 on 2007-01-16
come on, the default UBUNTU install creates this passwordless guest account and not one person can help me with this??????? what have others done?????

---

### Post by Biggus on 2007-01-16
Nothing. I didn't get a passwordless account with my install.

---

### Post by artinla on 2007-01-16
I have read something about /etc/shadow needing to contain a line such as:

root:*

The "*" is supposedly required for a null password.

I have not made this work but it might point you in the right direction.

Art

---

### Post by dannyboy79 on 2007-01-17
> **Biggus said:**
> Nothing. I didn't get a passwordless account with my install.


so what is the password for your guest account then??? cause my system was installed with a passwordless guest account. Maybe this was done when I installed another application? I don't know. so what would happen if I delete it then??? or what would happen if I create a password for it. I have to ask since I don't know your experience level, are you sure you don't have a passwordless guest account? or are you just saying this cause that's what you hope and think is the case??? can you show me the output of 

sudo cat /etc/shadow

and if your scared to show me this then delete all your users except for the "nobody account". thanks

---

### Post by Biggus on 2007-01-19
I didn't get any guest account installed.

I got 

a) A Root user account (the account I use when I use sudo, so I understand)
b) My own user account (the one I sign into at the login screen)

and that's it. There were no other accounts created. That's from and Edgy 6.10 Main Live-CD.

My own level of experience is pretty low, I have to admit.

I'm trying to post my output from
> 
sudo cat /etc/shadow

but the board is telling me that

> You have included 18 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Images include use of smilies, the vB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

So I'll see if I can post up a screenshot or something instead.

---

### Post by dannyboy79 on 2007-01-19
> **Biggus said:**
> I didn't get any guest account installed.

I got 

a) A Root user account (the account I use when I use sudo, so I understand)
b) My own user account (the one I sign into at the login screen)

and that's it. There were no other accounts created. That's from and Edgy 6.10 Main Live-CD.

My own level of experience is pretty low, I have to admit.

I'm trying to post my output from


but the board is telling me that



So I'll see if I can post up a screenshot or something instead.

alright, you do have a guest account installed, it's just not named guest, in Ubuntu it's name is nobody. but after looking at your pic, your nobody account does have a password though. so I am trying to figure out why mine doesn't??? maybe I removed the password when I was having trouble setting up samba?? i don't know. so do you even know your password for your nobody account?? you can see if you do by going to the command line and typing su nobody, then it'll ask you for nobody's account password. (nobody's meaning the account nobody). Actually this is weird, I jsut tried it myself and when I just hit enter when it asks for nobody password it states authentification error. This is what my shadow file looks like for nobody;
nobody::13455:0:99999:7:::

I though maybe because mine has nohting in between the first 2 colons that that meant theres no password plus chkrootkit is telling me that account nobody doesn't have a password but now that I relook at the other entries in the shadow file, some have "!" and some have "*" and my main user and my root account have "$1$qImiBWlF$ojmz/hIU0s.i28Rqjes900" which I believe it a form of encryption so you can't read them obviously. so can anyone else help me figure out what I should put for nobody's account password so that is't back to the way Dapper is right after install???

---

### Post by lamego on 2007-01-19
I do not believe any application would change your nobody password, more probably it was your action.

> lamego@lamego-desktop:~/upgrade$ sudo grep nobody /etc/shadow
nobody:*:13480:0:99999:7:::
lamego@lamego-desktop:~/upgrade$ 


---

### Post by dannyboy79 on 2007-01-19
> **lamego said:**
> I do not believe any application would change your nobody password, more probably it was your action.


you are probably correct. also you'll notice in my last post that I have already stated this, "maybe I removed the password when I was having trouble setting up samba??" 

but my main question now is how do I change it back to whatever it was when I first installed ubuntu??? because now if I make it have a password so chkrookit shuts up, inside /etc/shadow file it now looks just like the main account, root account, ftp account, and others where it has that long encrypted number in between the first 2 colons. is this ok?? how come system created accounts have a "*" representing their password? and more importantly what are their passwords when the system creates the user????? do you know your nobody accounts password???

---

