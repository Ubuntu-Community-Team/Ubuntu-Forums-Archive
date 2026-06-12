---
title: "help with a few samba questions please."
date: 2022-07-21
forum: General Help
---

### Post by mason64 on 2022-07-21
Hey All 

Am trying to setup a samba server on ubuntu 22.04 server

installed samba, can get it working if the other machine connecting to it via windows has the same username and password as a samba user but cant with any other user. 

a few questions i cant work out 

[LIST=1]
[*]Where is it best to store network shares (what location on the server) i currently have a share under my main user ( This is not a prod server  just me messing about learning how to use samba, how it works and how to set it up)
[*]what permissions do i give to the shared folder for example do i keep the user as the owner of the folder and the folder set as group samba?
[*]is there a web site that can give me a good samba.conf or explain what the main settings are that are good to go?
[/LIST]

Sorry i hope that makes sense. windows user for 25 years plus fixing computers and now when am about to hit 40 i decide everything i use is linux (so am getting my grips to everything as quickly as possible).

Thanks for reading.

---

### Post by rsteinmetz70112 on 2022-07-21
First how have you set the samba server up? Is it set up as a member of an existing domain or is it an Active Directory Server? 
As for location the shares can be anywhere. I usually place mine is a separate directory, if they are to be accesed by mutliple users.
Generally for a user to access the Samba share they must be a samba user or a user of the domain the samba server belongs to.
You may want to look into the Homes share which shares a users home directory and can be set to automatically mount it.

As always the answeres depend on what you are actually up to. You also may

---

### Post by ActionParsnip on 2022-07-21
I like to make a /shares folder right in the root of the file system. There is no best place to share. It's a file system. Share what you need access to remotely. This is the best solution for you.

You can use smbpasswd to set a samba password for your users, they can then authenticate against the service and you can then use standard Linux ACLs to control access.

smb.conf has example stanzas in the file itself. Lots of guides online including YouTube

---

### Post by Morbius1 on 2022-07-22
Just a note on your immediate symptom:
> installed samba, can get it working if the other machine connecting to it via windows has the same username and password as a samba user but cant with any other user. 
It's because you did this:
> Where is it best to store network shares (what location on the server) i currently have a share under my main user ( This is not a prod server just me messing about learning how to use samba, how it works and how to set it up)

It's not that you created a share of something in your home folder since that is permitted it's because of the permissions of the home folder itself in Ubuntu 22.04.

Run this command to find the permissions of your home folder:
```
ls -dl $HOME
```
It should come back with something like this:
> ~$ ls -dl $HOME
drwxr-x--- 5 tester tester 4096 May 13 19:33 /home/tester

The user tester can read/wite but access is denied at the Linux permissions level to everyone else. 

Samba permissions and Linux permissions have to be in sync so if you create a share of say your Documents folder in smb.conf like this:
> [Documents]
path = /home/tester/Documents
read only = no

Only one user will gain access to that share and that is tester.

If you want to connect to that share from a Windows user named agnes samba will allow it ( if agnes has ben added to smbpasswd ) but Linux will reject it since agnes will not get pass the /home/tester folder.

One way ( there are limitless variations in Samba ) is to make agnes appear to be tester - for this share:
> [Documents]
path = /home/tester/Documents
read only = no
**[COLOR="#0000CD"]force user = tester[/COLOR]**


Agnes will still be prompted for credentials to gain access but once it's accepted everything she does will be as user tester.
Remember to restart smbd when you edit smb.conf: ```
sudo service smbd restart
```

---

