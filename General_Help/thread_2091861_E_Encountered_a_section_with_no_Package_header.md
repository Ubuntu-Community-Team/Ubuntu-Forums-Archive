---
title: "E: Encountered a section with no Package: header"
date: 2012-12-06
forum: General Help
---

### Post by Graham C Williams on 2012-12-06
System: 12.10 64bit

Can anyonr help please?

sudo apt-get check gets me this:

> Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.


W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/Release](http://archive.canonical.com/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/Release](http://extras.ubuntu.com/ubuntu/dists/quantal/Release)  

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal/Release](http://gb.archive.ubuntu.com/ubuntu/dists/quantal/Release)  

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release](http://gb.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

---

### Post by ibjsb4 on 2012-12-06
You have a mixed sources list of 12.04 and 12.10.  That needs to be corrected.  Remove all 12.04 sources and then try another update.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by Graham C Williams on 2012-12-06
Many Thanks.

Are all the 12.04 sources those that are mentioned as incorrect then?
Can I just delete them from the other sources list or does bash have some magic that will correct these things in the wink of Rudolf's eye?


Graham.

P.S. Does it change things that I like to use the Gnome interface?

---

### Post by ibjsb4 on 2012-12-06
The 12.04 sources will all have the word "precise" in them.  Also you could just uncheck them if you are unsure.  Unchecking them will remove them from your sources list and if a mistake is made, you can correct it easily.

Do an update from terminal afterwards to see any other errors that may exist.

```
sudo apt-get update
```

And no, this should not affect your current desktop.

Are you sure your running 12.10?  In terminal:

```
cat /etc/issue
```

---

### Post by Graham C Williams on 2012-12-07
Hello again.
> 
-8930:~$ cat /etc/issue
Ubuntu 12.10 \n \l

As to the other things.
I can no longer open:
"Update Software"
"Software sources"
or 
"Synaptic"
as I try and open them they report a similar error.

The example below is from synaptic.

> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

After this the application closes.

Any further suggestions please.
Graham.

---

### Post by ibjsb4 on 2012-12-07
In terminal:

```
sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update
```

---

### Post by Graham C Williams on 2012-12-07
Many Thanks.

That's done it. All appears to be working correctly.

What do you think had happened?

Once again, many thanks.

Graham.

---

### Post by ibjsb4 on 2012-12-07
Here's my secret  :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened&as_qdr=all&sa=Google+Search&lang=en)

---

