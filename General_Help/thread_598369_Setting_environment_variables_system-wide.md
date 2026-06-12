---
title: "Setting environment variables system-wide"
date: 2007-10-31
forum: General Help
---

### Post by mikyt on 2007-10-31
Hi everybody!

I have a problem setting environment variables that are valid for all the system.
I know that I can set an env variable by typing:
  export VARNAME=value
and this will last as long as the shell it's been typed in.
I also know that writing the same line in ~/.bashrc will make that variable available to every shell of the system.
But both of these situations are not what I need.
I want to write a script that, once executed (and only starting from that moment, not before), sets an environment variable for EVERY shell and every program opened from that moment on, until the system is halted or the variable is explicitly removed by another script.
Is that possible?

E.g.: I set http_proxy in a shell, inside a script. Then I open another shell and use apt-get through the proxy that I have set up.


Anyone knows how to do it?

---

### Post by ddrichardson on 2007-10-31
/etc/bash.bashrc is the system wide bashrc file.

---

### Post by bingoUV on 2007-10-31
/etc/bashrc is for all users who use bash shell.

/etc/profile is for all users using whatever shell

hope this helps

---

### Post by ddrichardson on 2007-10-31
> **bingoUV said:**
> /etc/bashrc is for all users who use bash shell.

/etc/profile is for all users using whatever shell

hope this helpsSorry to be contradictory, but according to the man page that is no longer the case - I have no idea when it changed, from the man page:
> /etc/profile
              The systemwide initialization file, executed for login shells
       /etc/bash.bashrc
              The systemwide per-interactive-shell startup file

---

### Post by bingoUV on 2007-10-31
hey, thanks for letting me know. Does not work in fedora / RHEL4. Seems to be an debian thing, is it? I see such a file in knoppix too.

---

### Post by mikyt on 2007-10-31
Thanks for all the answers, but they were not right for my question! :-) 
Probably what I wrote wasn't the right question. I try again, hoping to be clearer, describing the exact situation I want to solve.

I have a local network at home. I can connect to it using my router and all works well.
Then, there is my university network: here I have to use a proxy server, so I have to set http_proxy.

If I set it in bashrc or in profile, the proxy will be set even when I'm at home and, obviously, I won't be able to use the network, since that proxy is only accessible from the university local network, so using that files doesn't seem to be an option.

I have a bash script I use to connect to my university network. If I use 
export http_proxy=ip_addr 
in that script and I run the script with
. networkScript
or
source networkScript
I am near to the solution, since I'm able to use the network from the terminal where I've run the script and form every program that I start from that terminal, but still there is a thing I can't do: if I start a program from the system menu (let's say Adept, Synaptics, or whatever) it won't be able to access the network, nor will a different terminal will.

What I would like, is a way to set the http_proxy variable so that I can open a terminal, run my network script, than close the terminal and start an application from the system menu (or another terminal) that can access the network. 
Then, when I use the disconnect script, I can unset the http_proxy variable, go back home and use my network without any proxy.

Is this feasible in some way?

Have I got to modify the connection script so that it will edit the bashrc file adding the http_proxy definition and the disconnect script will remove it?
I think it would be a very unclean approach and I hope there is a better way to solve this problem!

---

### Post by Deived on 2007-11-01
I think I'm looking for the same thing, but for Oracle.

When I try to use the Oracle command 'imp' or 'exp', it doesnt find the command.  However when I set variables in the shell that I got from the Oracle site, it works, but just in that terminal window.  How can I get those variables set system wide?

Here's the script from Oracle I used to set the variables.

```
ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server
export ORACLE_HOME
ORACLE_SID=XE
export ORACLE_SID
NLS_LANG='$ORACLE_HOME/bin/nls_lang.sh'
export NLS_LANG
PATH=$ORACLE_HOME/bin:$PATH
export PATH
if [ $?LD_LIBRARY_PATH ]
then
	LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH
else
	LD_LIBRARY_PATH=$ORACLE_HOME/lib
fi
export LD_LIBRARY_PATH
```

How can I get these paths set system wide?

Can I just stick this code in one of those files?  Or is there a better way
(I'm a bit of a newb, but have been running Linux as my main desktop for a few months now)

---

### Post by mikyt on 2007-11-02
> **Deived said:**
> I think I'm looking for the same thing, but for Oracle.
[...]
Can I just stick this code in one of those files? 

It's not the same thing I'm looking for, but you're lucky. If I understood well what you need, you just need to paste that piece of code in /etc/bash.bashrc (if you want it to be valid for every user) or in /.bashrc (if it has to be valid just for you) and you're done, since you do not seem to have to activate/deactivate the variables like I do.

---

### Post by MWt on 2008-07-18
From 
[https://help.ubuntu.com/community/EnvironmentVariables#System-wide environment variables]("https://help.ubuntu.com/community/EnvironmentVariables#System-wide environment variables")
I have found that putting a new file (with path to libraries) into /etc/ld.so.conf.d/ is also a good idea - maybe even preferred?

And do not forget to run 'ldconfig' as the last step!

---

