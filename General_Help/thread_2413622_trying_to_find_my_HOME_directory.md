---
title: "trying to find my HOME directory"
date: 2019-02-27
forum: General Help
---

### Post by Skaperen on 2019-02-27
in a case where i am juggling some user sessions, the value of the HOME environment variable is lost.  so, i am trying to set it back.  the "pwd" command gives the current directory, which is not the user's HOME.  the ~ symbol maps into the same thing.  the "cd" command with no argument gives an error message saying "cd: HOME not set".

**how can i find the _HOME directory_ for the current user in this situation?**

---

### Post by bitsnpcs on 2019-02-28
Hello Skaperen,

this discusses how to lists all local users and edit users [https://askubuntu.com/questions/410244/a-command-to-list-all-users-and-how-to-add-delete-modify-users](https://askubuntu.com/questions/410244/a-command-to-list-all-users-and-how-to-add-delete-modify-users)

Once you know a users name one way you can find the users directory is by using their username as a search term, or additionally browsing to a file in a directory where you know a file belongs to that user, if you click on a file to highlight it, then right click the file and select properties , this will list -
Parent Folder: /home/username/directory-name
where the file is located that you have clicked, and so it gives the path, to the user home directory.

There are many search tools, I like Fsearch most out of those I have tried so far, I use it on my other desktop (Ubuntu 16.04 based distro) how to install Fsearch -
[https://www.omgubuntu.co.uk/2016/11/file-search-app-fsearch-now-ppa](https://www.omgubuntu.co.uk/2016/11/file-search-app-fsearch-now-ppa)

Checking, it says suport for Ubuntu 18.04 added [https://github.com/cboxdoerfer/fsearch/issues/132](https://github.com/cboxdoerfer/fsearch/issues/132)

---

### Post by The Cog on 2019-02-28
Looking in /etc/passwd will give you everybody's home directory. 
Or this command will print it:
```
grep $(whoami) /etc/passwd | cut -d: -f6
```
It calls whoami to find the user's name, searches for the line in /etc/passwd and picks out the 6th field.

---

### Post by HermanAB on 2019-02-28
'ls /home' will usually also give everyone's user name and home directory.

---

### Post by Skaperen on 2019-02-28
> **bitsnpcs said:**
> Hello Skaperen,

this discusses how to lists all local users and edit users [https://askubuntu.com/questions/410244/a-command-to-list-all-users-and-how-to-add-delete-modify-users](https://askubuntu.com/questions/410244/a-command-to-list-all-users-and-how-to-add-delete-modify-users)

Once you know a users name one way you can find the users directory is by using their username as a search term, or additionally browsing to a file in a directory where you know a file belongs to that user, if you click on a file to highlight it, then right click the file and select properties , this will list -
Parent Folder: /home/username/directory-name
where the file is located that you have clicked, and so it gives the path, to the user home directory.

There are many search tools, I like Fsearch most out of those I have tried so far, I use it on my other desktop (Ubuntu 16.04 based distro) how to install Fsearch -
[https://www.omgubuntu.co.uk/2016/11/file-search-app-fsearch-now-ppa](https://www.omgubuntu.co.uk/2016/11/file-search-app-fsearch-now-ppa)

Checking, it says suport for Ubuntu 18.04 added [https://github.com/cboxdoerfer/fsearch/issues/132](https://github.com/cboxdoerfer/fsearch/issues/132)

sorry for not expressing this ... i mean in a programming or scripting context, not an interactive context.  i am working on creating virtual background sessions to start programs in and it will have an option for root to do this as any user.

---

### Post by Skaperen on 2019-02-28
> **HermanAB said:**
> 'ls /home' will usually also give everyone's user name and home directory.

that definitely does *not* work on my system which has /home and /home2 where some users are on one and some are on the other.

---

### Post by HermanAB on 2019-03-01
You can use a wildcard.

---

### Post by #&amp;thj^% on 2019-03-01
This "might" work for you:
```

homedir=$( getent passwd "$USER" | cut -d: -f6 )
```

This will also work on users that are not you. For instance,
```

homedir=$( getent passwd "someotheruser" | cut -d: -f6 )
```

---

