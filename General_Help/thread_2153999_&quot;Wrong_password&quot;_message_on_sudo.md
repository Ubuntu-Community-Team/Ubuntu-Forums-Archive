---
title: "&quot;Wrong password&quot; message on sudo"
date: 2013-06-13
forum: General Help
---

### Post by NautiusMaximus on 2013-06-13
I'm in the process of setting up an Ubuntu 12.04 server, and I'm experiencing some weird behaviour.

If I try to execute a command via sudo, I am asked for my password in the normal way, but then when I enter my password I receive the message "Wrong password".

However, it's not wrong. Not only am I pretty sure I'm typing it carefully, but the command executes anyway.

Now, this is not actually preventing me doing anything, since it seems I can just ignore the message and everything works just fine. But it bothers me that I'm getting the message, and suggests that maybe something is wrong that's going to come back and cause problems later.

Any ideas?

Thanks
NM

---

### Post by HiImTye on 2013-06-13
what command are you running? it could be that a second command is failing to authenticate, and not your initial one. in 12.10 sudo prints
```
Sorry, try again.
```I'm not sure if it is the case in 12.04[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by NautiusMaximus on 2013-06-13
I've tried it for a whole load of different commands. Always the same result. Message is "Wrong Password", but the command executes anyway.

---

### Post by HiImTye on 2013-06-13
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
do you have root's password enabled?

---

### Post by NautiusMaximus on 2013-06-14
I don't think so. At least I haven't knowingly done anything to enable it, and unless I've misunderstood how these things work, it's disabled by default, right?

Just a thought, but I think this may have something to do with enabling shares with Windows machines, where the security is controlled by a Windows server. The problem seems to start after I set that bit up.

---

### Post by NautiusMaximus on 2013-06-18
Bump?

---

### Post by NautiusMaximus on 2013-06-25
Bumpity bump?

---

### Post by steeldriver on 2013-06-25
Are you seeing anything that might give any hints in /var/log/auth.log (stuff like pam_ldap maybe)?

---

### Post by NautiusMaximus on 2013-06-25
Thanks for that suggestion.

Yes, I think I am indeed seeing something that might give hints, though what exactly they're hinting at I'm not sure. When I try to run a command as sudo I don't see anything that looks like an error, but when I log on (via ssh) in the first place, then I do see some things that don't look right. Here is what the auth.log looks like when I log on;

```
Jun 25 16:19:50 localhost sshd[1907]: pam_winbind(sshd:auth): getting password (0x00000180)
Jun 25 16:19:51 localhost sshd[1907]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_AUTH_ERR (7), NTSTATUS: NT_STATUS_LOGON_FAILURE, Error message was: Logon failure
Jun 25 16:19:51 localhost sshd[1907]: pam_winbind(sshd:auth): user '[username]' denied access (incorrect password or invalid membership)
Jun 25 16:19:51 localhost sshd[1907]: pam_winbind(sshd:account): user '[username]' granted access
Jun 25 16:19:51 localhost sshd[1907]: Accepted password for [username] from 192.168.98.6 port 42698 ssh2
Jun 25 16:19:51 localhost sshd[1907]: pam_unix(sshd:session): session opened for user [username] by (uid=0)

```

Does that help narrow down what the problem might be?

Thanks 
NM

---

### Post by HiImTye on 2013-06-25
> **NautiusMaximus said:**
> ```
Jun 25 16:19:51 localhost sshd[1907]: pam_winbind(sshd:auth): user '[username]' denied access (incorrect password or invalid membership)
```

that looks to be your problem, sshd is denying you
at least it does if it coincides with your terminal messages
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Impavidus on 2013-06-25
> **HiImTye said:**
> what command are you running? it could be that a second command is failing to authenticate, and not your initial one. in 12.10 sudo prints
```
Sorry, try again.
```I'm not sure if it is the case in 12.04

It's the same in 12.04, so either it isn't sudo that complains (if it did, the command shouldn't run), or you have some kind of modified sudo that prints the "Wrong password" message by default, whether the password be right or wrong.

What happens when you deliberately enter a wrong password?

---

### Post by NautiusMaximus on 2013-06-25
> **Impavidus said:**
> It's the same in 12.04, so either it isn't sudo that complains (if it did, the command shouldn't run), or you have some kind of modified sudo that prints the "Wrong password" message by default, whether the password be right or wrong.

What happens when you deliberately enter a wrong password?

Well, that turns out to be a rather interesting question. It wasn't what I expected.

What happens is I get the same "Wrong password" message, but then it prompts for my password again. No surprises so far.

If I then enter the **correct** password at the second attempt, it then says "Sorry, try again", and then prompts again. At the third attempt (the 2nd time of entering the correct password), it says "Wrong password" and then executes the command anyway.

Weird.

---

### Post by NautiusMaximus on 2013-06-25
> **HiImTye said:**
> that looks to be your problem, sshd is denying you
at least it does if it coincides with your terminal messages
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

OK, so I did the experiment of logging directly into the terminal rather than doing it by SSH. I got exactly the same result (with "login" substituted for "sshd" in the log file), so I don't think this is an SSH problem.

---

### Post by furtom on 2013-06-25
I had this exact problem once in a while on 12.04. It was very odd, indeed. I had found that a reboot solved it. I later discovered my HD had bad sectors, so I attributed the problem to that. After I replaced the disk and re-installed, I never had this problem again.

---

### Post by HiImTye on 2013-06-25
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
without knowing more about what you're doing when you get the errors, it's very difficult to diagnose your problem.

---

### Post by NautiusMaximus on 2013-06-26
> **furtom said:**
> I had this exact problem once in a while on 12.04. It was very odd, indeed. I had found that a reboot solved it. I later discovered my HD had bad sectors, so I attributed the problem to that. After I replaced the disk and re-installed, I never had this problem again.

Don't think it's likely to be anything to do with bad disk sectors. I have exactly the same problem on 2 different machines that I've set up in the same way.

---

### Post by NautiusMaximus on 2013-06-26
> **HiImTye said:**
> [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
without knowing more about what you're doing when you get the errors, it's very difficult to diagnose your problem.

I get the errors whenever I type a command starting with "sudo" and enter my password. It doesn't matter what the command following "sudo" is, the behaviour is always the same. I get a "Wrong password" message, but the command executes anyway.

Is there anything more I can tell you?

---

### Post by steeldriver on 2013-06-26
You mentioned setting up some Windows share stuff - do you remember the details? in particular did you mess with /etc/nsswitch or any of the files in /etc/pam.d?

---

### Post by NautiusMaximus on 2013-06-26
Yes, indeed I did. I messed with /etc/nsswitch.conf and with 3 of the files in /etc/pam.d: common-account, common-auth, common-session.

Is this beginning to sound like a PAM problem?

---

### Post by steeldriver on 2013-06-26
Well tbh I know squat about PAM but my guess would be that because /etc/pam.d/sudo includes the common-xxxx defs, something about the module ordering in your common-auth file is causing your (local) sudo password to be passed to the pam_winbind.so module when it shouldn't be

---

### Post by NautiusMaximus on 2013-06-26
Yeah, I know squat about PAM as well, and I'm beginning to think that could be the cause of my problems here. :oops:

Anyway, this is what my common-auth file looks like (some of the commented lines removed for brevity):

```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#


# here are the per-package modules (the "Primary" block)

auth	sufficient pam_winbind.so krb5_auth krb5_ccache_type=FILE 

auth	sufficient pam_unix.so nullok_secure use_first_pass 



#auth	[success=3 default=ignore]	pam_krb5.so minimum_uid=1000
#auth	[success=2 default=ignore]	pam_unix.so nullok_secure try_first_pass
#auth	[success=1 default=ignore]	pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth	optional			pam_smbpass.so migrate
# end of pam-auth-update config
```

Any obvious problems with that that anyone can spot?

---

### Post by steeldriver on 2013-06-26
I *think* that says to try winbind auth first, and fall back to local (pam_unix.so) auth if winbind fails - which would somewhat jive with the behavior you're seeing

However I don't know enough about your setup or why you changed it to know whether that's the desired order or not - my impression from the docs is that the pam.d file(s) should be autogenerated by pam-auth-update (either manually or as part of a package install) rather than edited directly these days

---

### Post by NautiusMaximus on 2013-06-26
OK, so I did the experiment, and swapped those first 2 lines over. Wasn't quite what I was expecting. I now need to enter my Windows password to log on. If I try entering my Ubuntu password, it doesn't let me in.

Now here's the odd thing. With those 2 lines swapped over, I can authenticate a sudo command using either my Windows or Ubuntu password, but if I use the Ubuntu password, I get the "Wrong password" message.

---

### Post by NautiusMaximus on 2013-06-26
And now I've done the obvious next experiment, and swapped those 2 lines back again. Now it turns out I can log in with either my Windows or Ubuntu password, and can also authenticate sudo commands with either. If I use my Windows password to authenticate, then I don't get the "Wrong password" message.

I feel we're homing in on a solution here, though my lack of understanding of how PAM works means that I'm probably going to need a bit more help yet.

---

### Post by steeldriver on 2013-06-26
Just swapping the lines probably wont work right - it's supposed to chain through the modules so for example you likely don't want use_first_pass in the first module stanza

You seem quite gung-ho about changing configs so you could maybe just back up 

```

/etc/pam.d/common-auth
/etc/pam.d/common-session
/etc/pam.d/common-password
/etc/pam.d/common-account
/etc/pam.d/common-session-noninteractive

```

and then run 

```
sudo pam-auth-update
```

and make sure all the modules are selected (here is mine from a 12.04 desktop machine with samba)

```

 |    
[*] Unix authentication                                                &#9474;  
 &#9474;    
[*] Winbind NT/Active Directory authentication                         &#9474;  
 &#9474;    
[*] GNOME Keyring Daemon - Login keyring management                    &#9474;  
 &#9474;    
[*] ConsoleKit Session Management                                      &#9474;  
 &#9474;    
[*] Inheritable Capabilities Management                                &#9474; 

```

That should generate a 'clean' PAM config - if your Windows shares stop working, we can then get one of the Samba experts to address that separately

---

### Post by NautiusMaximus on 2013-06-26
> **steeldriver said:**
> 

You seem quite gung-ho about changing configs



I am indeed, but that's because I'm doing all this on a test installation. The consequences are pretty minimal if I bugger everything up completely.

Anyway, thanks for the suggestion: will give all that a try and see where we end up.

---

### Post by NautiusMaximus on 2013-06-26
OK I've tried the steps you suggest. It hasn't actually got rid of my "Wrong password" message, and it's also borked my Samba sharing: I can no longer connect to Samba shares using a Windows password as I should be able to.

The options I had were not the same as yours. Here's what I saw:

```
 PAM profiles to enable:                                                   &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;    [*] Kerberos authentication                                            &#9474;  
 &#9474;    [*] Unix authentication                                                &#9474;  
 &#9474;    [*] Winbind NT/Active Directory authentication                         &#9474;  
 &#9474;    [*] SMB password synchronization                                       &#9474;  
 &#9474;                                                          
```

Any ideas where we go from here?

Thanks
NM

---

### Post by NautiusMaximus on 2013-06-26
Sorry, ignore me. It didn't bork my Samba sharing at all, it was my own stupidity that did that. Forgot that I'd disabled it on the test system. Have enabled it again and it now works after running pam-auth-update.

However, I'm still getting the "Wrong password" message.

---

### Post by steeldriver on 2013-06-26
Did it actually alter your pam.d files? maybe it doesn't overwrite them if it finds manual changes

I guess the next step depends how much you trust your original source for the changes you made - to my (inexpert) eye, they look kind of odd for a 'modern' config - I would have expected something using the [result=action] syntax like the commented out bits

For reference, here's how mine looks - I have never edited it by hand afaik

```

# here are the per-package modules (the "Primary" block)
auth    [success=2 default=ignore]      pam_unix.so nullok_secure
auth    [success=1 default=ignore]      pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
# here's the fallback if no module succeeds
auth    requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth    optional                        pam_cap.so
# end of pam-auth-update config

```

The way I read it, it tries regular pam_unix auth first, if that succeeds it skips over winbind (and deny...); else it tries winbind, initially with the same password you supplied for unix auth (try_first_pass) then prompting for a separate winbind password if that fails; if it succeeds it skips over deny.

---

### Post by NautiusMaximus on 2013-06-26
Yes, it did change the config files. My common-auth file now looks like this (again, some commented out bits removed for brevity):
```

#
# /etc/pam.d/common-auth - authentication settings common to all services
#


# here are the per-package modules (the "Primary" block)
auth	[success=3 default=ignore]	pam_krb5.so minimum_uid=1000
auth	[success=2 default=ignore]	pam_unix.so nullok_secure try_first_pass
auth	[success=1 default=ignore]	pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth	optional			pam_smbpass.so migrate
# end of pam-auth-update config
```

Although running pam-auth-update hasn't yet fixed the "Wrong password" problem, it does seem to have fixed the [other, far more serious, problem I've been having with cron jobs]("http://ubuntuforums.org/showthread.php?t=2157466"). So whether or not this is on the way to fixing the "Wrong password" problem, I am nonetheless hugely grateful that you suggested it!

---

