---
title: "Nvu"
date: 2006-10-03
forum: General Help
---

### Post by cssutto on 2006-10-03
I gave up on Amaya and decided on Nvu.

I am having problems with the ftp entry that needs to be made to log on.

My ISP says that [ftp://ftp.suttonmachine.com](ftp://ftp.suttonmachine.com) should get me there and I think it does because I get the message "login incorrect".

I have entered my name and password exactly as I do in FrontPage.

Any ideas?

CSSJR

---

### Post by Herman on 2006-10-04
Hello, cssutto,
I make all my web pages with NVU. I don't use the 'File'-->'Publish' option at all though, I have never tried it out. 
I just have an icon on my desktop that I can open. It requires a password to open it, and, once opened, it seems very similar to a regular folder in my own computer, except it is really in my ISP's (Telstra Bigpond Australia)'s server. I can just drag and drop or copy and paste the .html files, and associated folders with image files into it.

To set that up, once the website was set up with my ISP, I set up the FTP networking connection in something like the following manner,

I went:
1) 'Places', 'Connect to Server', 
2) 'Connect to Server' window opens,
Service type, (spinbox)->FTP (with login)
Fill in fields for:
Server: ftp.websitename.com 
Port: 21 (at least for me it is 21)
Folder: (In my case I leave this one blank)
Username:  (insert your username)
Name to use for connection: (make something up here)

3)You should get an FTP icon on your desktop.
Right-click on the  FTP icon and click 'Open'.

4) Type your website password and save it in the keyring

5) Type your keyring password to unlock your keyring.

6) Your website should open.
It will appear the same as an empty folder, you just drag and drop into it whatever pages you want to publish, and the images that go with them.
I find it best to have the images in folders, one for each webpage.

I never unmount or delete the folder icon on my desktop, it remains there after each reboot, and just needs to be opened with the keyring each session. 

I hope that will be of some help to you,

Regards, Herman :D

---

### Post by cssutto on 2006-10-04
I appreciate the help, but it turned out that the web site was never set up for ftp.

It was set up by an employee who is no longer here so we had to do a little detective work.

Contact with the ISP insisting that he check the validity of the password led to the ftp discovery.

So now I am connected, but not able to look at any of the files.

This site was set up with FrontPage and I have used W2K and FrontPage many times to modify and add to the site, so the site is working.

I read somewhere that with Nvu, I can look at and edit files that were created with FrontPage.  So far, I am not able to do so.

I hope I can.  I don't want to start from scratch and build a new site.

CSSJR

---

