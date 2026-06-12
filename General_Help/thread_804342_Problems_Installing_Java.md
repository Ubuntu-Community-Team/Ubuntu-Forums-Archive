---
title: "Problems Installing Java"
date: 2008-05-23
forum: General Help
---

### Post by severvip on 2008-05-23
I'm having trouble install Java to Ubuntu 8.04. Originally I was getting an error running fakeroot, but I realize I was logged in as root in terminal. So I exited root and I'm still getting errors. 

[COLOR="Gray"]user@my-laptop:~$ cd /home/user[/COLOR]

To get myself into my user folder because that is where I have the Java rpm.bin file. Nothing seems to happen when I type that though. I still get this.

[COLOR="Gray"]user@my-laptop:~$[/COLOR]

I guess I'm going to assume I'm in my user folder, even though it doesn't say.

[COLOR="Gray"]user@my-laptop:/home/user#[/COLOR]

Okay so now I type the fakeroot stuff and this is what appears.

[COLOR="Gray"]user@my-laptop:~$ fakeroot make-jpkg jre-6u6-linux-i586-rpm.bin

Creating temporary directory: /tmp/make-jpkg.yaEGvC9436
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

Detected Debian build architecture: i386
Detected Debian GNU type: i486-linux-gnu

No matching plugin was found.
Removing temporary directory: done[/COLOR]

What am I doing wrong, I can't figure it out. Any help is much appreciated.

Severvip

---

### Post by PmDematagoda on 2008-05-23
Did you try install Java using the repositories with:-
```
sudo apt-get install sun-java6-jre sun-java6-bin
```

---

### Post by FuturePilot on 2008-05-23
First, yes you are already in your home directory. That is where you start out every time you open a terminal. You can check this by entering
```
pwd
```
That prints the working directory.

Second, Ubuntu does not use RPM. It uses DEB as it's based on Debian. You can very easily install Java as well as a bunch of other goodies like audio codecs and Flash Player by installing the ubuntu-restricted-extras package. You can go Applications&#8594;Add/Remove and search for ubuntu-restricted-extras or just paste this in the terminal.
```
sudo apt-get install ubuntu-restricted-extras
```

:)

---

### Post by barnex on 2008-05-23
A remark on the above posts: installing ubuntu-restricted-extras will give you an openJDK-based java, while sun-java6-* will give you the 'official' version of sun. The fist one is totally open source and works well 99% of the time, sun's version however turned out to be a lot faster on my machine and may even be more reliable. The choice is yours.

If you install both, you can set the default java with ```
sudo update-alternatives --config java
```

---

### Post by FuturePilot on 2008-05-23
> **barnex said:**
> A remark on the above posts: installing ubuntu-restricted-extras will give you an openJDK-based java, while sun-java6-* will give you the 'official' version of sun. The fist one is totally open source and works well 99% of the time, sun's version however turned out to be a lot faster on my machine and may even be more reliable. The choice is yours.

If you install both, you can set the default java with ```
sudo update-alternatives --config java
```

It does? Hmmm they must have changed that. I didn't know that. Thanks. I will keep that in mind.

---

