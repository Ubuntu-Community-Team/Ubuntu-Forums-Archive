---
title: "apt-get Could not resolve ':@'"
date: 2006-12-11
forum: General Help
---

### Post by haimroman on 2006-12-11
When I try to run "apt-get install" or "apt-get upgrade", I get the following message:

[INDENT]Could not resolve ':@'[/INDENT]

Here is an example of the command & output:

```

# apt-get install traceroute
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  traceroute
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.2kB of archives.
After unpacking 106kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  traceroute
Install these packages without verification [y/N]? y
Err http://il.archive.ubuntu.com edgy/main traceroute 1.4a12-20
  Could not resolve ':@'
Failed to fetch http://il.archive.ubuntu.com/ubuntu/pool/main/t/traceroute/traceroute_1.4a12-20_i386.deb  Could not resolve ':@'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Trying --fix-missing did not help.  Nor is the problem only with il.archive.ubuntu.com.  When I try an uptdate, I get the message also for the other site in my /etc/apt/sources.list:

```

# apt-get update
Err http://security.ubuntu.com edgy-security Release.gpg
  Could not resolve ':@'
Err http://il.archive.ubuntu.com edgy Release.gpg
  Could not resolve ':@'
Ign http://security.ubuntu.com edgy-security Release
Err http://il.archive.ubuntu.com edgy-updates Release.gpg
  Could not resolve ':@'
Ign http://security.ubuntu.com edgy-security/main Packages
Err http://il.archive.ubuntu.com edgy-backports Release.gpg
  Could not resolve ':@'
...

```

I've searched google & this forum, & have found instances of "coule not resolve", but it was always followed by a host name.  I don't know where this ":@" is coming from.  I've checked all the files under /etc/apt/.  Any ideas?

Thanks

---

### Post by bapoumba on 2006-12-11
Please open a terminal and paste the output of
```
cat /etc/apt/sources.list
cat /etc/apt/apt.conf
cat /etc/environment
```

Are you behind a proxy ?

---

### Post by haimroman on 2006-12-11
Thanks for the reply.  No, I'm not behind a proxy.

Here are the contents of the files.  I also ran "cat -ev" on them, but did *not* find any hidden non-printable characters.


**/etc/apt/sources.list**

```

deb http://il.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://il.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://il.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://il.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://il.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://il.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://il.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://il.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

**/etc/apt/apt.conf** - I don't have one.  I do have the following files under 
/etc/apt/apt/conf.d:

**/etc/apt/apt.conf.d/01ubuntu**:
```

APT
{
  NeverAutoRemove  
  { 
	"^linux-image.*";  
	"^linux-restricted-modules.*";
  };

  Install-Recommends-Section "metapackages";
};

```

**/etc/apt/apt.conf.d/05aptitude**:
```

aptitude::Keep-Unused-Pattern "^linux-image.*$ | ^linux-restricted-modules.*$";

```

**/etc/apt/apt.conf.d/10periodic**:
```

APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";

```

**/etc/apt/apt.conf.d/20archive**:
```

APT::Archives::MaxAge "30";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "500";

```

**/etc/apt/apt.conf.d/50unattended-upgrades**:
```

// allowed (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
	"Ubuntu edgy-security";
//	"Ubuntu edgy-updates";
};

// never update the packages in this list
Unattended-Upgrade::Package-Blacklist {
//	"vim";
};

```

**/etc/apt/apt.conf.d/70debconf**:
```

// Pre-configure all packages with debconf before they are installed.
// If you don't like it, comment it out.
DPkg::Pre-Install-Pkgs {"/usr/sbin/dpkg-preconfigure --apt || true";};

```

**/etc/apt/apt.conf.d/99update-notifier**:
```

DPkg::Post-Invoke {"if [ -d /var/lib/update-notifier ]; then  touch /var/lib/update-notifier/dpkg-run-stamp; fi";};

```

**/etc/environment**
```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_US.UTF-8"
LANGUAGE="en_US:en"

```

---

### Post by bapoumba on 2006-12-11
Well, the ':@' is puzzling me ... Not sure where this could come from.

Your sources.list is ok.
/etc/apt/apt.conf is absent, that is normal if you are not behind a proxy. Double check with > System > Prefs > Network proxy that "direct internet connexion" is ticked.

Have you ever been able to perform updates ? Has anything changed ? How do you connect to internet ? Apt has problems with some routers (D-link for ex.). I suppose that Firefox is working ok.

Have you tried to remove the "il" in your source.list and use the general *.ubuntu.com repositories ?

---

### Post by haimroman on 2006-12-11
Some peole here solved the problem.

I had the following environment variable:

[INDENT]http_proxy=http://:@:3128/[/INDENT]

This came about because I was trying the different Gnome graphical settings, including the one for network proxy.  Somehow, it got to the state where:
[LIST]
[*]the host name of the proxy was blank
[*]the port was set to 3128
[*]In the Details windows, use authentication was checked
[*]however, the user name & password were blank
[/LIST] 

Afterwards, I checked direct connection to the internet instead of use a proxy, but the environment variable still got set.  After unsetting the environment variable, it was OK.

---

