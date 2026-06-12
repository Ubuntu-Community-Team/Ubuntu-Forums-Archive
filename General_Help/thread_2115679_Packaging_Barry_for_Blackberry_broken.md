---
title: "Packaging Barry for Blackberry broken?"
date: 2013-02-13
forum: General Help
---

### Post by Mark_in_Hollywood on 2013-02-13
I'm attempting an install of software for the Blackberry Smartphone. 

According to the page:

[http://www.netdirect.ca/software/packages/barry/installdebian.php](http://www.netdirect.ca/software/packages/barry/installdebian.php)

Where it says:

To install the latest version of Barry onto Debian Squeeze, add the following line to your /etc/apt/sources.list file:

deb [http://download.barry.netdirect.ca/barry-latest/](http://download.barry.netdirect.ca/barry-latest/) squeeze main

There are multiple versions of **Ubuntu** available. Replace the word "squeeze" above with one of the following:

...

ubuntu1204

I ran the

 gpg --keyserver pgp.mit.edu --recv-key B6C2250E
        gpg --armor --export B6C2250E > barry.key
        apt-key add barry.key

and saw no problems:

mark@Lexington-19:~$ gpg --keyserver pgp.mit.edu --recv-key B6C2250E
gpg: requesting key B6C2250E from hkp server pgp.mit.edu
gpg: key B6C2250E: public key "Chris Frey (NetDirect Barry Key) <cdfrey@foursquare.net>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
mark@Lexington-19:~$ gpg --armor --export B6C2250E > barry.key
mark@Lexington-19:~$ apt-key add barry.key
ERROR: This command can only be used by root.
mark@Lexington-19:~$ sudo apt-key add barry.key
OK

Next:

On running

sudo aptitude upate

sudo aptitude install barry, the terminal said

W: Failed to fetch [http://download.barry.netdirect.ca/barry-latest/dists/ubuntu1204/Release](http://download.barry.netdirect.ca/barry-latest/dists/ubuntu1204/Release)  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

I then ran sudo aptitude update and saw there were available upgrades, ran that and saw

E: Failed to fetch [http://download.barry.netdirect.ca/barry-latest/dists/ubuntu1204/main/binary-i386/libtar-dev_1.2.16-1_i386.deb:](http://download.barry.netdirect.ca/barry-latest/dists/ubuntu1204/main/binary-i386/libtar-dev_1.2.16-1_i386.deb:) Got a single header line over 360 chars
E: Unable to correct for unavailable packages

How can I clean up the mess this has made, download the tarball and compile it, etc. per:

[http://www.netdirect.ca/software/packages/barry/install.php](http://www.netdirect.ca/software/packages/barry/install.php)

what direcory is that to go in so that the files/folders/stuff is correctly installed and loaded?

---

### Post by Mark_in_Hollywood on 2013-02-13
AND then, several hours later, I found this:


[http://www.netdirect.ca/software/packages/barry/installdebian.php](http://www.netdirect.ca/software/packages/barry/installdebian.php)

which SOLVES this thread.

I apologize, Linux Community

---

