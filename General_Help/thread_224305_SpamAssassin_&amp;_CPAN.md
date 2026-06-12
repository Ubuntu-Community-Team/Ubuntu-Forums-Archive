---
title: "SpamAssassin &amp; CPAN"
date: 2006-07-27
forum: General Help
---

### Post by Riverside on 2006-07-27
Having recently migrated from SuSE 9.2 to Dapper, I am having issues with the almost prehistoric SpamAssassin version packaged for Dapper (and all other Ubuntu releases in fact, even Edgy Eft has only 3.1.0 packaged as per Dapper, about as much use as a fly swatter in a gunfight given the pace of change in the spam arena since 3.1.0 was released on 2005-09-14).

In an attempt to upgrade to SpamAssassin 3.1.4 released yesterday, I used CPAN (as I used to do with SuSE).  I first installed Bundle::CPAN and then ran (as root of course):

cpan> install Mail::SpamAssassin                                                
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Thu, 06 Jul 2006 13:28:59 GMT
Mail::SpamAssassin is up to date (3.001004).

Clearly, CPAN isn't functioning correctly, and is only able to read an old version of /root/.cpan/Metadata presumably created when the final release of Dapper was built.

Does anyone with more Perl knowledge than I know how to (correctly) remedy this?

Alternatively - can Ubuntu's SpamAssassin package maintainer keep at least reasonably up to date with SpamAssassin releases please?!

---

### Post by Riverside on 2006-07-29
In fact, it appears that an earlier attempt to update SpamAssassin by downloading the 3.1.4 source code from the SpamAssassin web site, running perl Makefile.PL followed by make and then sudo checkinstall, which failed with a checkinstall error message, did not entirely fail and that some parts of the new module had been installed.  Most confusing.

Anyway, after much trial and error, the following appears to be a way of installing SpamAssassin and subsequently keeping it updated on a Dapper system.  There may be better ways, as I am not an expert in this area.

Firstly:

```
sudo apt-get install spamassassin spamc
```
Next, immediately:

```
sudo apt-get remove spamassassin spamc
```
Why do this?  To install needed configuration files /etc/default/spamassassin & /etc/init.d/spamassassin which are needed to run spamd (the daemonized SpamAssassin binary) on an Ubuntu Dapper system (apt-get remove leaves installed configuration files in place).

Next, use CPAN to obtain, build and install the latest SpamAssassin version.

```
sudo perl MCPAN -e shell
o conf prerequisites_policy ask
install Mail::SpamAssassin
quit
```
The first time that CPAN is run, is it necessary to configure the module, however the dialogue automatically presented should be self-explanantory.

It is also not a bad idea to update the CPAN bundle itself, using install Bundle::CPAN.

Once the latest SpamAssassin version 3.1.4 has been downloaded, it is necessary to do:

```
sudo ln -l /usr/bin/spamd /usr/sbin/spamd
```
This is necessary as the CPAN downloaded SpamAssassin source code results in installation of the spamd binary in /usr/bin/spamd, whereas the Ubuntu package maintainer places it in /usr/sbin/spamd, and as a result /etc/init.d/spamassassin references DAEMON=/usr/sbin/spamd (alternatively, one could edit /etc/init.d/spamassassin of course).

Next, use the sa-update program to obtain the very latest SpamAssassin rule updates (it is a good idea to do this weekly at least, as spammers continually update their technique to defeat filtering tools such as SpamAssassin, and as a result this is something of an arms race):

```
sudo sa-update -D
```
The program will exit with an exit code (but only if the -D flag is used, so it is recommended to do so) of 0, which means that updates were available and downloaded, or 1, which means that no fresh updates were available.

Finally, start the newly installed spamd daemon:

```
sudo /etc/init.d/spamassassin start
```

---

### Post by dajhorn on 2006-11-24
Doing this prior makes the SpamAssassin upgrade easier:

  $ sudo apt-get build-dep spamassassin

However, you must have the appropriate deb-src lines in the '/etc/apt/sources.list' file, which can be added through System -> Administration -> Synaptic Package Manager.

---

