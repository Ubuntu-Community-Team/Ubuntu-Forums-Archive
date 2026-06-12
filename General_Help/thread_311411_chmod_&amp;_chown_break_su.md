---
title: "chmod &amp; chown break su"
date: 2006-12-02
forum: General Help
---

### Post by pwykersotz on 2006-12-02
I've been having a serious problem with Edgy lately and I finally tracked down the source.  Whenever I recursively modify my /etc directory with 777 permissions or change ownership to my user account, it breaks su.  If I want to launch a program that has root permissions (such as Guarddog or Adept Package Manager) or want to use the Actions > Edit as Root option for a file, it returns the error "Su returned with an error".  This happens for the whole system, not just for files within the changed directory.

I would very much like to keep user permissions for /etc.  It makes my life a lot easier.  This did not happen for me in Dapper.  Any suggestions?  Is there a single directory that holds a vital su component that I can just avoid changing?

Thanks ahead of time.

---

### Post by taurus on 2006-12-02
It is never a good thing to "chmod -R 777 /etc" in Ubuntu or Linux in general!!!  Those files have certain permissions for a reason and if you are not sure what you are doing, you can crash the whole system...  If you need to run or modify something outside of your own $HOME directory, use sudo...  That's why the first user on the system is added to groups adm & admin for that purpose.

---

### Post by pwykersotz on 2006-12-02
I am aware of the dangers, but I still need to know what breaks su.  This is more about me knowing what will and won't break my system than security.

---

### Post by aysiu on 2006-12-02
> **pwykersotz said:**
> I am aware of the dangers, but I still need to know what breaks su.  This is more about me knowing what will and won't break my system than security.
It could be any number of things, but my guess is the /etc/sudoers file, which is supposed to be 440, not 777. Of course, it could also be /etc/passwd or /etc/shadow or /etc/.pwd.lock

Seriously, take taurus' advice--leave the filesystem permissions alone unless you know what you're doing. They are set up that way for a reason.

If you want to make your life easier *and* have a functioning system, read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by PilotJLR on 2006-12-02
I agree - the sudoers file must have proper permissions.

setting 777 on /etc/* is a very, very bad idea.

---

