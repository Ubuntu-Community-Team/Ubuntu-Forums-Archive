---
title: "Converting .rpm to .deb problem"
date: 2013-03-09
forum: General Help
---

### Post by catalinc on 2013-03-09
Hello

[COLOR=#808080]I am a new ubuntu user. My main reason for switching to ubuntu was to get used to use autodesk maya under linux. I followed this guide to install Maya [/COLOR][[COLOR=#808080]http://rajivpandit.wordpress.com/2012/10/03/how-to-install-maya-2012-64bit-linux-mint-13-or-ubuntu/[/COLOR]]("http://rajivpandit.wordpress.com/2012/10/03/how-to-install-maya-2012-64bit-linux-mint-13-or-ubuntu/")[COLOR=#808080]. I think maya was installed, but I never managed to get the soft running. For some reason, I was missing libtiff.so.3 and all attempts to link libtiff.so.4 or another library were in vain. I found a script on github to install maya2013, but that didn't work either. Script I used: [/COLOR][[COLOR=#808080]https://gist.github.com/heiths/3250500[/COLOR]]("https://gist.github.com/heiths/3250500")

The main problem is that for some reason, alien cannot convert .rpm to .deb, but it worked before I tried running the script.
This is what comes up now in terminal when I try converting any rpm:
```
    chmod 755 -/./
chmod: invalid option -- '/'
Try `chmod --help' for more information.
    mkdir -/debian
mkdir: invalid option -- '/'
Try `mkdir --help' for more information.
mkdir -/debian failed:  at /usr/share/perl5/Alien/Package/Deb.pm line 299.
    find - -type d -exec chmod 755 {} ;
    rm -rf -

```
I am running Ubuntu 12.10 x64.
I tried uninstalling alien and reinstalling it, but the problem persists. I remember that I installed ubuntu tweaks and synaptic manager before trying the script.
I don't know if its because the script is for v12.10, because of what I installed or maybe something else.

If anyone has any idea of what to do, then please let me know before I try installing maya on Linux Mint.
Thank you.

---

### Post by schragge on 2013-03-09
Try calling *alien* manually:
```

sudo apt-get install fakeroot
fakeroot alien -cv $HOME/MAYAINSTALL/*.`arch`.rpm
```

[highlight]Update.[/highlight]
I doubt you really have any file names beginning with **-** in any of the rpms, but there's some excessive use of sudo in the script, like
```
sudo for i in $INSTALLDIR/*.rpm; do sudo alien -cv $i; done
```I wonder if this could be related to the error somehow. If converting the rpms manually works then edit the script and change the line shown above to:
```
fakeroot alien -cv $INSTALLDIR/*.`arch`.rpm
```
or rather comment it out as you will already have the rpms converted, and conversion takes a sizable time.

---

### Post by catalinc on 2013-03-09
Thanks for the reply.

I have been trying to convert manually after the first time I tried the script. It did not work.
I tried with fakeroot as well. same thing.
This is the whole output from terminal.
```

cc@cc-Aspire-6920:~/maya$ fakeroot alien -kv Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm
	LANG=C rpm -qp --queryformat %{NAME} 'Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm'
	LANG=C rpm -qp --queryformat %{VERSION} 'Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm'
	LANG=C rpm -qp --queryformat %{RELEASE} 'Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm'
	LANG=C rpm -qp --queryformat %{ARCH} 'Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm'
	LANG=C rpm -qp --queryformat %{CHANGELOGTEXT} 'Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm'
	LANG=C rpm -qp --queryformat %{SUMMARY} 'Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm'
	LANG=C rpm -qp --queryformat %{DESCRIPTION} 'Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm'
	LANG=C rpm -qp --queryformat %{PREFIXES} 'Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm'
	LANG=C rpm -qp --queryformat %{POSTIN} 'Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm'
	LANG=C rpm -qp --queryformat %{POSTUN} 'Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm'
	LANG=C rpm -qp --queryformat %{PREUN} 'Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm'
	LANG=C rpm -qp --queryformat %{LICENSE} 'Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm'
	LANG=C rpm -qp --queryformat %{PREIN} 'Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm'
	LANG=C rpm -qcp 'Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm'
	rpm -qpi 'Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm'
	LANG=C rpm -qpl 'Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm'
	mkdir -
	chmod 755 -
	rpm2cpio Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm | lzma -t -q > /dev/null 2>&1
	rpm2cpio Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm | (cd -;  cpio --extract --make-directories --no-absolute-filenames --preserve-modification-time) 2>&1
Unpacking of 'Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm' failed at /usr/share/perl5/Alien/Package/Rpm.pm line 168.
	find - -type d -exec chmod 755 {} ;
	rm -rf -

```

---

### Post by cmcanulty on 2013-03-09
have you seen this?
[http://www.ubuntugeek.com/package-converter-frontend-for-alien.html]("http://www.ubuntugeek.com/package-converter-frontend-for-alien.html")

---

### Post by schragge on 2013-03-09
This is strange. I've just downloaded Maya 2013 tarball, and successfully converted all *.x86_64.rpm files to .deb. However, the rpm in your output is named Maya[COLOR=#ff0000]2011[/COLOR]*.rpm Are you sure you've downloaded the right tarball? Also, I don't see anything with *_docs_* in its name in my download. Have you tried alien on some rpms you know it worked before? 

Also, do you have $RPMBUILDOPTS and/or $RPMINSTALLOPT defined?

---

### Post by catalinc on 2013-03-09
@cmcanulty I installed the package. Ubuntu said it was 'bad quality', but went through any way. It doesn't want to start up...

@schragge
I have 2011,2012 and 2013 versions of maya. Yes, I am that serious. I tried a 2011 rpm to see if it was any different. 
How do I check if $RPMBUILDOPTS and/or $RPMINSTALLOPT are defined?

---

### Post by schragge on 2013-03-09
```
echo $RPMBUILDOPTS
echo $RPMINSTALLOPT
```

Another thought. I have the package *lzma* installed on my system, so when alien unpacks an rpm it uses it, and not the lzma emulation provided by xz.

---

### Post by catalinc on 2013-03-09
Aparently lzma is not installed and the echo commands return a blank line.
I do have liblzma5 though.

---

### Post by schragge on 2013-03-09
TBH, I don't think anymore that lzma is involved: I've just rpm2cpio Maya2013*.rpm and the output is not lzma-compressed. Please try
```
fakeroot alien -k --veryverbose Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm
```

[highlight]Update.[/highlight]
Also, please post the output of the following commands
```

LANG=C rpm -qp --qf %{name}\\n Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm
LANG=C rpm -qp --qf %{version}\\n Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm

```

---

### Post by catalinc on 2013-03-09
When I execute fakeroot alien -k --veryverbose Maya2011_0-docs_en_US_64-2011-88.x86_64.rpm I get all the lines like this one:
```

cpio: ./usr/autodesk/maya2011-x64/docs/Maya2011/en_US/style/tech.js: Function open failed: Permission denied

```
And the end is like my second post ...line 168
If I execute with sudo instead of fakeroot, I get all the lines like this one:
```

cpio: ./usr/autodesk/maya2011-x64/docs/Maya2011/en_US/style/tech.css not created: newer or same age version exists

```
And the ending is the same as my first post ...line299.

When I execute the LANG lines, nothing is returned.

---

### Post by schragge on 2013-03-09
> **catalinc said:**
> When I execute the LANG lines, nothing is returned. Aha, that's the problem. You should get the name and the version of the rpm package. On my system (Debian wheezy):
```

[COLOR=green]$[/COLOR] rpm -qp --qf %{name}\\n Maya2013_0_64-2013.0-299.x86_64.rpm
[COLOR=#008000]Maya2013_0_64[/COLOR]
[COLOR=green]$[/COLOR] rpm -qp --qf %{version}\\n Maya2013_0_64-2013.0-299.x86_64.rpm
[COLOR=#008000]2013.0[/COLOR]

```
Does quoting the format string help?
```
rpm -qp --qf [COLOR=#ff0000]'[/COLOR]%{name}\n[COLOR=#ff0000]'[/COLOR] Maya*.rpm
```
Also, what does *printenv | grep ^RPM* show?

---

### Post by catalinc on 2013-03-09
I don't get anything with  printenv | grep ^RPM.

---

### Post by schragge on 2013-03-09
What's with quoting the rpm format string?

At this point, I'd rather reinstall all rpm-related stuff anyway
```

sudo apt-get --reinstall --only-upgrade install ^{lib,}rpm

```

---

### Post by catalinc on 2013-03-09
Quoting doesn't do anything either. I'll try reinstalling to see if anything changes.
Thanks for your help.

---

### Post by catalinc on 2013-03-09
It seems that the rpm stuff were the problem.
Thank you again.
Can you give points or something to helpful users on these forums?

---

### Post by schragge on 2013-03-09
[highlight]Edit.[/highlight] Sorry, I misunderstood your question as "Can you give some help points for other users?" :)

Sure. For each rpm file on command line, *alien* creates a temporary directory like [COLOR=blue]name[/COLOR][COLOR=red]-[/COLOR][COLOR=blue]version[/COLOR] and unpacks contents of the rpm there. The [COLOR=blue]name[/COLOR] and the [COLOR=blue]version[/COLOR] parts are what alien gets by running *rpm -qp --queryformat* with appropriate rpm tags (%{NAME} and %{VERSION}) on the rpm file. In your case, the verbose output of alien was like
```

mkdir [COLOR=red]-[/COLOR]
...
cd [COLOR=red]-[/COLOR]

```
whereas it should be like
```

mkdir Maya2011_0-docs_en_US_64[COLOR=red]-[/COLOR]2011
...
cd Maya2011_0-docs_en_US_64[COLOR=red]-[/COLOR]2011

```
Note also, that *cd -* is equivalent to *cd $OLDPWD*.

That is clearly a problem with *rpm -qp --queryformat* returning nothing.

---

### Post by catalinc on 2013-03-09
:)
It doesn't seem possible to give you points or votes directly, but have a 1UP from me.

---

