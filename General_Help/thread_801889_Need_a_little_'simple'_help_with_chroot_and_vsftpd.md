---
title: "Need a little 'simple' help with chroot and vsftpd please"
date: 2008-05-21
forum: General Help
---

### Post by cackles on 2008-05-21
This is probably really easy stuff so if someone could please help me out and tell me how to get the list of all the functions etc. from the commands 'command --help' just isnt cutting it, Id appreciate it. Im pretty new at this with a lot to learn. Im just trying to setup some ftp stuff but I keep screwing with folders and having to reinstall cus I dunno how to view the permissions or how to change them, probably simple stuff.

How does the whole www folder thing work? I created a user for ftping it and made their home /var/www but I believe that folder is supposed to be owned by apache? How could I check the settings of that folder and get my ftp account to add, delete and modify? I think I need to add it to the same group as apache and set the permissions that way but Im unsure how exactly. I dont really want to chown it in case apache and whatever else needs to cant access it.

Edit: I used ls -l to find it was in the group root owned by root and changed the file folder permission to 774 then added my ftp login to that group and can do stuff ok now. Is that an ok thing to do? The account is stuck in its home directory but it now means that login could be used to do all the funky stuff root can ... if it can be executed fast enough ... right? I probably got that totally wrong.

I read about making a user in the vsftpd config file.

# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.

How is that achieved? Is that just a user with a password or no password and no home folder? I have a user currently with no pass and no folder, it just says login incorrect when I try to login with it so I dunno if vsftpd is actually using it.

---

### Post by fsmithred on 2008-05-22
Instead of "comand --help" try "man command". For example, "man ls" or even "man man".

Putting your user into the root group is probably not a good idea. Isn't there an ftp group? 

It's been awhile since I've played with vsftpd, but I recall that you can't log in with the unprivileged ftpuser. It gets a little confusing when you start messing with the chroot and umask options. That's about all I can offer with any certainty.

---

### Post by bingoUV on 2008-05-22
1. Why must you use /var/www directory to store your ftp files? You could use any other directory. vsftpd uses /var/ftp/ by default for its anonymous ftp. Use it if you are using anonymous ftp. For non-anonymous, create any directory, set any permissions and owner.

2. vsftpd might start as root, and immediately drop its privileges to the ftp user. This way, it does not need to "login", the account need not have a password, shell or a home directory but the process runs as the low privilege ftp user.

It is not clear what you want to achieve. State it out clearly so someone here might help you out more completely.

---

### Post by cackles on 2008-05-28
Its a headless 8.04 install, I am looking to upload my web pages to my www folder folder by using an FTP prog from an XP machine. I was worried that if I had changed the ownership of the folder to an FTP account I created specifically for doing that it would stop the webserver from working, Ive found that is not the case and after creating the new user and chown to the new www ftp account it all still works fine. I made the vsftpd config chroot all accounts.

I take it this is because Apache etc. runs from root, though Im not sure.

I havent tried anything fancy with it, just simple webpages. I dont know if I do put anything fancy in, like a feedback/contact form, if it will still work because I havent got that far.

Im pretty new to this and sorry if Im not clear.

If I got something wrong or havent explained properly again please let me know.

---

### Post by bingoUV on 2008-05-29
> **cackles said:**
> 
I take it this is because Apache etc. runs from root, though Im not sure.



It is customary to run Apache as root. Apache configuration file has a user to which it drops its privileges immediately upon invocation so that you will mostly not find a running Apache server running from root account.

Besides that, I don't understand you.

Do you want to use a web server or ftp? Both? Title says vsftpd so maybe you do not want to use web server at all. Don't start Apache at all in that case. Apache does not help vsftpd in running. vsftpd is capable of running on its own.


If you want to use both Apache and vsftpd, keep them separate. I do not see any need for you to keep ftp user's home directory /var/www. This is used by Apache. Why do you want to mix the directories used by these two things? Let ftp user own ftp directory, Apache user own /var/www directory. Where is the problem?

---

### Post by cackles on 2008-05-29
I want to run Apache for the site and upload the html/php files for the site via ftp.

It will be me uploading the html/php to the www folder but I setup a new user so my main account doesnt need to go there.

Its not an ftp dump, its just for the html/php and any other files for the site I will be building.

---

### Post by bingoUV on 2008-05-29
Oh. Now I see.

Try using apache as the ftp user. Even if it does not work, no problem. I have run apache with /var/www folder owned by another user. It works well.

---

### Post by cackles on 2008-05-29
Thanks for the help, as long as I know Im not putting anything at risk Im fine with that.

I made sure of the permissions ... 755 (I think, cant remember off top of my head)

---

