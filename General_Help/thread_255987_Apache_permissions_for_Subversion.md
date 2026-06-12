---
title: "Apache permissions for Subversion"
date: 2006-09-12
forum: General Help
---

### Post by Thyamine on 2006-09-12
Hey all,

I've been fighting to get Subversion working on Ubuntu, and I believe I have most things setup.  However trying to import files into the repository brings up an error and seems to indicate that Apache (I'm accessing the repository through http) doesn't have permission to write to the location which is at /svm/repos.

How do I give Apache write access there?  I did a chmod 777 just to try and resolve the issue but that didn't work.  Somewhere I saw about changing the owner and group to 'apache', but there is no user on the system called 'apache'.  I installed Apache from apt-get.  How do I determine what user/context Apache is running in so I can give that access to write to my repos folders?

](*,)

---

### Post by bwaskiew on 2006-10-09
Hey there,

I've been having the same exact problem. Everything can communicate fine, but when I try to import something into the repository, it gives me a permission denied when trying to create a new folder in the 'db' directory.

I performed the steps listed at
[https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)
especially pertaining to the Server Configuration section, like creating the SVN repository and setting the permissions.

I'll keep an eye on this thread to see if anyone resolves the issue.

---

### Post by jessecollins on 2006-11-01
Have you guys changed ownership of the repository so that Apache can write to it?

Try this command:

```
sudo chown -R www-data:www-data /svn
```

Note: Change "/svn" to the location of your Subversion repository.

I have also written my own tutorial [here]("http://www.jessejcollins.com/blog/index.php?/archives/32-Setup-Subversion-with-Apache2-on-Ubuntu.html").  Maybe it could be useful.

Hope this helps.  ;)

---

### Post by matthewstory on 2006-11-01
yeah, www-data is the apache user in Ubuntu so you'll want to try that, make sure you're using chown -R and chmod -R for recursive on the entire svn directory tree.  In addition you'll want to check out the permissions specifically on the /svn/db folder and its contents, this is usually the place where permissions errors in subversion come from.

Have you considered using svnserve as opposed to apache.  I believe it has HTTP support, also support for svn+ssh.

---

### Post by jessecollins on 2006-11-02
I just created a script that will automate the installation and setup of Subversion and Apache2.  It can be found [here]("http://www.jessejcollins.com/blog/index.php?/archives/37-Script-for-Installing-Subversion-on-Ubuntu.html").

---

