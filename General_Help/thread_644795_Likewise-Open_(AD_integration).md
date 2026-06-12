---
title: "Likewise-Open (AD integration)"
date: 2007-12-19
forum: General Help
---

### Post by markusfarkus on 2007-12-19
I am not sure if this is the best place to post this, but it is an interesting and unique problem.  

I am currently testing out the new likewise-open product [http://www.likewisesoftware.com/community/index.php/download](http://www.likewisesoftware.com/community/index.php/download)

I am wondering if anyone else has tried this product out?  I  am having limited success with the product.  It installs on 32 bit with no problem and I can compile it for 64 bit.  The machines do get added to the AD and I can log in as an AD user and can even lock things down by group.  My problem is when I open a terminal it hangs and eventual reports random errors.  I can ctrl-c out, but there are a few random other things that aren't working like they should.  

I am just wondering if anyone else has tried the product out and if you ran into the same problems.  If not I am very curious what your environment is like.   

Thanks

---

### Post by markusfarkus on 2007-12-19
Update:  I found out that Ubuntu will be including the code from likewise-open in their next version.  Can anyone confirm this?

I heard that it will be part of samba is Ubuntu going to do any tweaking?  Have you guys started testing yourself?  Have you run into these problems?

---

### Post by HermanAB on 2007-12-19
See this: [http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

It may clear up some questions.

Cheers,

Herman

---

### Post by markusfarkus on 2007-12-19
Yea I have seen these type of solutions and we have deployed them with some limited success.  I appreciate the link...I'll look into it.

I think I am looking for someone else who has specifically tried likewise.  My boss really likes the product and its simplicity...as noted by the link you provided there is a lot of trial and error and headaches.  This likewise product installed without hitch and added a computer with no problems.  It even allows cached credentials.  My only problem is when I open a terminal or run things like groups.  So if anyone has run openlikwise let me know.

On that note you should look into this product.  It looks very slick and is quite easy.  If it truly becomes a part of Ubuntu it will surely make things easier for us.  Of course there are plenty of bugs that need to be worked out.

Thanks again!

---

### Post by HermanAB on 2007-12-19
Note that integration with AD is only an issue if you insist on using Ubuntu.  Mandriva has a wizard for it.  So, you could install Mandriva and a few clicks later you are done.

---

### Post by astabeno on 2008-03-10
Likewise Open was included in the universe repository for Ubuntu 8.4 Hardy Heron.

[http://packages.ubuntu.com/hardy/net/likewise-open-gui](http://packages.ubuntu.com/hardy/net/likewise-open-gui)

---

### Post by Rever75 on 2008-04-22
I am using likewise-open from in Hardy from the repo. I was able to join my Laptop to the domain and log in with my AD User. However, I cannot add myself to any groups on the local machine. IE. virtualboxusers group Any help would be great.

---

### Post by markusfarkus on 2008-04-22
You can add your AD account to the sudoers file.  I haven't tested this with virtualbox, but if you had to you could just run it as root.

---

### Post by gotee12 on 2008-04-28
I found this tip in the comment section of [this]("http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/") site....

If you go into your sudoers file (visudo from a CLI) like markusfarkus suggested, but add:

```
%*YOURDOMAINNAME*\\domain^admins ALL=(ALL) ALL
```

Then all domain admins that log into the Ubuntu machine will have sudo priveledges. Of course you could use any group from your domain, not just the domain admins. But pay attention to include the double "\\" after your domain name and be sure to use the "^" to signify spaces in the group name.

The only thing that annoys me is that I still have to re-create some shortcuts such as "Synaptic Package Manager" and whatnot. Anybody know why these root-type app shortcuts are not automatically created even if the person is a sudoer?

---

### Post by markusfarkus on 2008-04-28
I believe that you could manually edit the /etc/group file as well.  So you can edit virtual box by appending your username to the end of the line like so.

virtualbox:x:125:user,domain\user

Note that I don't know what the group name for virtual box is so make sure you are editing the right group. I would try that and see if it helps you out.

---

### Post by adwatkin19 on 2008-07-03
I am a teacher, and myself and one of the ICT bods are currently investigating this software and the possibility of rolling out UBUNTU across the whole school. 

We got the software installed, that was fine, (32bit OS just in case anyone was interested) when we rebooted, we couldnt log in with our AD credentials, had to log in a normal user, then logout and log in, so changed the run level of the program, this corrected this problem.

We have got to a stage where we now need to mount specific windows shares dependant on the user that is logged in. To do this we decided to use the domainjoin-cli query command to get the information from the server, and then to use this to connect to specific shares. So we attempted to run the command domainjoin-cli query, but you have to be in the sudoers file to run this. We dont want any old kid in school being able to do anything so this isnt an ideal situation for us. 

We also though about writing a bash script that runs just after logging in to pick up the details needed and then mounting accordingly. Would this work? and if not, is there other ways to get the distinguished name etc from the server?

Thanks alot 

Adam

---

### Post by markusfarkus on 2008-07-03
Have you thought about using autofs?  The setup I have uses autofs...one thing though is that we are running services for Unix on our windows machines so we can share out the windows shares via NFS.  That may not be possible in your situation.  

You can also give students specific sudo rights just to mount.  Sudo doesn't have to give total control if you don't want it to.

---

### Post by adwatkin19 on 2008-07-07
The NFS and AutoFS isn't really an option with the way the network is setup, and the network bods are a little resistant to our attempts to try this sort of thing. 

But basically is there a way to get information like the distinguished name etc with out running domainjoin-cli query as this requires the admin privileges,

---

