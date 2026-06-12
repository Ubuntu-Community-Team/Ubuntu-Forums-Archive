---
title: "Downloading specific version of sudo 1.8.27 Overwriting current version."
date: 2022-05-30
forum: General Help
---

### Post by ramesh8 on 2022-05-30
[COLOR=#000000]I have A current version of sudo which 1.9 version . 

Code:
No LSB modules are available.


Distributor ID:    Ubuntu


Description:    Ubuntu 22.04 LTS


Release:    22.04


Codename:    jammy


Linux test-VirtualBox 5.15.0-33-generic #34-Ubuntu SMP Wed May 18 13:34:26 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]

[COLOR=#000000]Here's the error i am getting[/COLOR]

[COLOR=#000000]Code:
sudo make install


if test -d ./.hg && cd .; then \


    if hg log --style=changelog -b default > ChangeLog.tmp; then \


	mv -f ChangeLog.tmp ChangeLog; \


    else \


	rm -f ChangeLog.tmp; \


    fi; \


elif test -d ./.git && cd .; then \


    ./log2cl.pl -b master > ChangeLog; \


else \


    echo "ChangeLog data not available" > ChangeLog; \


fi


for d in lib/util  plugins/group_file plugins/sudoers plugins/system_group src include doc examples; do \


    (cd $d && exec make pre-install) && continue; \


    exit $?; \


done


make[1]: Entering directory '/home/test/Downloads/sudo-1.8.26/lib/util'


make[1]: Nothing to be done for 'pre-install'.


make[1]: Leaving directory '/home/test/Downloads/sudo-1.8.26/lib/util'


make[1]: Entering directory '/home/test/Downloads/sudo-1.8.26/plugins/group_file'


make[1]: Nothing to be done for 'pre-install'.


make[1]: Leaving directory '/home/test/Downloads/sudo-1.8.26/plugins/group_file'


make[1]: Entering directory '/home/test/Downloads/sudo-1.8.26/plugins/sudoers'


Checking existing sudoers file for syntax errors.


/bin/bash: line 3: ./visudo: No such file or directory


make[1]: *** [Makefile:384: pre-install] Error 127


make[1]: Leaving directory '/home/test/Downloads/sudo-1.8.26/plugins/sudoers'


make: *** [Makefile:103: pre-install] Error 2[/COLOR]
[COLOR=#000000]I downloaded the files for 1.8.26 version from here [/COLOR][https://www.sudo.ws/getting/download/](https://www.sudo.ws/getting/download/)[COLOR=#000000] then i ran this following command ./configure , make , then make install and it is getting while runnng make install i want to overwrite the current version of sudo

Thank You [/COLOR]

---

### Post by TheFu on 2022-05-30
Please use code tags when posting code and/or terminal output.  
Code Tags: [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)

Also, we need the prompt so the exact PWD is known and the userid.

Going backward on a working release to an older sudo is a bad idea. It will likely break the OS.
What I'd do it install a 20.04 LXD container instance, then do any testing in that with the sudo v1.8.31 on that install.  LXD containers are really easy to setup, while providing enough of an OS to check stuff most people need.  If you need to check the specific v1.8.x version, it shouldn't be a big deal on 20.04, since only the 3rd version number is changing.

As for how to build software, that means you need to manually handle the required dependencies. Hopefully, those dependencies will be spelled out in the README for the package. 

Looks like visudo wasn't built.

Were any erorrs/warnings seen in the prior steps?

---

### Post by ramesh8 on 2022-05-30
No Error. But how can i go back to previous version of sudo with LXD i  think i will get a same error .

---

### Post by TheFu on 2022-05-30
> **ramesh8 said:**
> No Error. But how can i go back to previous version of sudo with LXD i  think i will get a same error .

What are the outside dependencies.  Between 20.04 and 22.04, lots of basic libraries have changed. I bet a few are incompatible with v1.8 in 22.04.

Is there a specific reason you want the older version?

---

### Post by #&amp;thj^% on 2022-05-30
Here is the error:
```
make[1]: Entering directory '/home/me/sudo-1.8.32/lib/util'
/bin/bash ../../mkinstalldirs /usr/local/libexec/sudo
mkdir /usr/local/libexec
mkdir: cannot create directory \u2018/usr/local/libexec\u2019: Permission denied
mkdir /usr/local/libexec/sudo
mkdir: cannot create directory \u2018/usr/local/libexec/sudo\u2019: No such file or directory
make[1]: *** [Makefile:286: install-dirs] Error 1
make[1]: Leaving directory '/home/me/sudo-1.8.32/lib/util'
make: *** [Makefile:169: install] Error 2

```
I can pretty much promise that you will break sudo.
If a downgrade is really important, you may find help here: [https://github.com/sudo-project/sudo](https://github.com/sudo-project/sudo)

---

### Post by ramesh8 on 2022-06-01
there was some vulnerbility with that sudo version so i  want ro see and analyze it  . i am very cuirious how sudo was exploited

---

### Post by TheFu on 2022-06-01
> **ramesh8 said:**
> there was some vulnerbility with that sudo version so i  want ro see and analyze it  . i am very cuirious how sudo was exploited

I'd definitely use lxd with the OS version selected running the correct dependencies then. There are hundreds of lxd how-to guides.  In 3 minutes, you can be logged into a minimal Linux server with your choice of version (assuming the version is still supported). If it is an ubuntu flavor, it will have a version of sudo.

sudo has many subtle security uses and considerations which are easy to lose.  There's always more to learn for sudo security, but many of the attacks are standard Unix attacks which have been understood for 30+ yrs.  

I vaguely recall the sudo issue from a few years ago.  After reading the detailed analysis about it, I knew it didn't apply to my systems in they way they are used. It was a local account escalation, I believe. 
[http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-3156](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-3156)

Another easy way to get the older code would be to install the 20.04 initial DVD ISO release from 2020.  Since this bug wasn't fixed until 2021, it will be inside that release.  Don't patch the system, obviously.

---

### Post by #&amp;thj^% on 2022-06-01
here is good site for that info: [https://nvd.nist.gov/vuln/detail/CVE-2019-14287](https://nvd.nist.gov/vuln/detail/CVE-2019-14287)

And the exploit: [https://www.exploit-db.com/exploits/47502](https://www.exploit-db.com/exploits/47502)
# Fix : The bug is fixed in sudo 1.8.28
# CVE : 2019-14287

This sounds very odd, since sudo has been fixed in newer versions.
**If your after cracking and hacking info, you won't find it here.**

---

