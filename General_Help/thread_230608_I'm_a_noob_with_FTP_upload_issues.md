---
title: "I'm a noob with FTP upload issues"
date: 2006-08-06
forum: General Help
---

### Post by jreid08 on 2006-08-06
:confused:  I can’t find documentation written at my level in the Wiki (some documentation is great and some not so good) dealing with permission issues and all of the postings that might be similar to my problem have replies written by Borg and I thought Ubuntu was written for humans:)  I'm having a problem uploading to my FTP server with Dreamweaver (I’m using VSFTPD).  I cannot upload anything to /var/www/ (I'm assuming that's the public_html that I'm usually accustom to on shared accounts that I've had in the past), however I can download.  This is the error that I get while using the only account I set up on my Ubuntu LAMP 6.06:

"index.html - error occurred - An FTP error occurred - cannot put index.html.  Access Denied.  The file may not exist, or there could be a permission problem.

File activity incomplete. 1 file(s) or folder(s) were not completed.

Files with errors: 1
index.html"

I’m also having trouble uploading with winSCP.  I can download however when I upload I get the following error:

"scp: /var/www/index.html: Permission denied"

I'm assuming that there is a permission, owner or group problem.  What's frustrating is that I can't grasp the permissions documentation I found in the Wiki.  FYI, I'm a total noob to Linux (I’m on day 4) and I like what I've been able to accomplish so far but I'm having a really slow go at it on FTP.  On the upside I've been able to set up and configure SSH so I haven't given up yet:)

I'd really appreciate some assistance/advice/instructions.

Thanks,
JR

---

### Post by HereInOz on 2006-08-06
I assume that you are attempting to upload a webpage to a remote hosting server?  Is that correct?

The easiest way to do that is to save the file to your home folder, or somewhere similar, then click on Places > Connect to Server.

This will give you the option of setting up a connection to a particular type of server, and one of the options is FTP (with Logon).  If you follow the prompts on this, entering the server name, username and ultimately password when it attemps to open the remote folder, you should be fine.

When you click on "Connect" it will place a folder on your desktop.  Double click on that, and it will ask for a password and that should get you in to the folder.  It is a "Drag and Drop" situation from there on.

If it doesn't work, you may have permission problems on your hosting server.

---

### Post by nix4me on 2006-08-06
You need to make sure /var/www is writeable by the user from which you are uploading from.

You also need to be sure that vsftpd is set up so that writing is enabled.  The default is NO uploads allowed.

nix4me

---

### Post by jreid08 on 2006-08-06
I should mention that I don't have the desktop installed.  I have the installation you get when you select "LAMP."

With that in mind, how do you see if folders and files are writeable?  Likewise, how do you change that and what would you want to change it to so that you're safe and not inadvertently allowing anyone to do anything they want with files and folders?

Thanks again all,
JR

---

### Post by jreid08 on 2006-08-10
> **nix4me said:**
> You need to make sure /var/www is writeable by the user from which you are uploading from.

You also need to be sure that vsftpd is set up so that writing is enabled.  The default is NO uploads allowed.

nix4me

So what do I type at the command line to make sure /var/www/ is writeable by a particular user?  Is that more secure or is it better to do it by group and if so then how do I do that rather than by user?  Is this going to be the same process for FTP as it is for SSH?

I'm fairly sure that I have the conf for vsftpd set correctly.

Thanks everyone!
JR

---

