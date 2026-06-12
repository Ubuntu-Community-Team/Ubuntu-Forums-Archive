---
title: "My Linux machine Hacked"
date: 2007-01-22
forum: General Help
---

### Post by r0ck80y on 2007-01-22
Hey !!

I am usin ubuntu 6.06 and recently a friend of mine  somehow uncovered my root password !!!   ](*,) 
 He refuses to divulge how he did that. AFAIK, the passwd/shadow files had their usual perms and i had allowed ssh login as root ( now i changed the appropriate line in /etc/ssh/sshd_config to disallow root ssh ). Is there anything else that might have made me vulnerable? and how he might have pulled off such a feat on a noob like me?
HELP !

P.S. I also have suse installed and its files are accessible in /suse folder

---

### Post by meng on 2007-01-22
Are you sure he found your password or is he just scaring you? Are you using a "strong" password or one that can be easily guessed? Anyway, if you're using Ubuntu, why do you have a root password, isn't root password disabled by default?

---

### Post by taurus on 2007-01-22
Did you happen to add him to groups adm & admin in /etc/group?  Look in there to see if his login name is on those two groups.

```
cat /etc/group
```
(adm's near the top while admin is located toward the end of that file.)

---

### Post by r0ck80y on 2007-01-22
```
Are you sure he found your password or is he just scaring you?
```
Yup, he sure knows...he spelt it out..every letter !! I'll admit my root pass wasnt very strong btw.

```
Did you happen to add him to groups adm & admin in /etc/group? Look in there to see if his login name is on those two groups
```
No i did not add him...and the output shows this:
```

adm:x:4:<my normal username>
:
admin:x:112:<normal user>

```

I am pretty sure he didnt know my root password. Yes, i use the same root pass for suse and ubuntu. So when i mentioned that he possibly read the suse passwd file, he claimed thats not the case and that he can unravel the root pass again... :confused:

---

### Post by Hossie on 2007-01-22
Did he already have access to your computer (as unprivileged user) or didnt he have access at all? I think there was a SuSE version where the shadow file was world-readable (at least thats the case on one of our SuSE servers at work). If not, the only way (I dont think he exploited some server software) would be SSH brute forcing. There's an easy way to prevent such thing (no, it's not really just preventing root login via ssh), try searching for DenyHosts for example.

And btw: Delete the hacked system as soon as possible, you dont know what keyloggers, rootkits and such are installed now.

---

### Post by majoridiot on 2007-01-22
> **Hossie said:**
> And btw: Delete the hacked system as soon as possible, you dont know what keyloggers, rootkits and such are installed now.

not only that, but make sure your new password is VERY strong and unique only to that admin
account.  your "friend" is playing with your head.  he either got your pass from the suse install
or did some variation of looking over your shoulder, etc.

in any event, time for a new install... and a new "friend".

---

### Post by ardchoille42 on 2007-01-22
> **r0ck80y said:**
> Hey !!

I am usin ubuntu 6.06 and recently a friend of mine  somehow uncovered my root password !!!   ](*,) 
 He refuses to divulge how he did that. AFAIK, the passwd/shadow files had their usual perms and i had allowed ssh login as root ( now i changed the appropriate line in /etc/ssh/sshd_config to disallow root ssh ). Is there anything else that might have made me vulnerable? and how he might have pulled off such a feat on a noob like me?
HELP !

P.S. I also have suse installed and its files are accessible in /suse folder

This is one of the reasons the root account is disabled by default in Ubuntu. If you enabled it, you made your system less secure than it would have otherwise been. Have a look at [this page]("https://help.ubuntu.com/community/RootSudo"). It's best to keep the root account disabled and use sudo. I have been using Ubuntu since Warty and have never need to enable the root account.

---

### Post by Hossie on 2007-01-22
> **ardchoille42 said:**
> This is one of the reasons the root account is disabled by default in Ubuntu. If you enabled it, you made your system less secure than it would have otherwise been. Have a look at [this page]("https://help.ubuntu.com/community/RootSudo"). It's best to keep the root account disabled and use sudo. I have been using Ubuntu since Warty and have never need to enable the root account.

Why is Ubuntu more safe? If you hack the normal account, you can use as much sudo as you like and thus "are root"? Where is the enhanced security? In guessing the username? :o

---

### Post by r0ck80y on 2007-01-22
> **Hossie said:**
> Did he already have access to your computer (as unprivileged user) or didnt he have access at all? I think there was a SuSE version where the shadow file was world-readable (at least thats the case on one of our SuSE servers at work). If not, the only way (I dont think he exploited some server software) would be SSH brute forcing. There's an easy way to prevent such thing (no, it's not really just preventing root login via ssh), try searching for DenyHosts for example.

And btw: Delete the hacked system as soon as possible, you dont know what keyloggers, rootkits and such are installed now.

Well he did use my computer thru my username login to scp some files, he may have sudo-ed to get some info...but still he decoded my root passwd and not the normal user one, and claims he can do it again....Anyway he'll be available tomm so i can garner some more info if possible but he wont reveal the trick to me unless i treat him with a king-size chicken burger. :biggrin:

DenyHosts?? Is that /etc/hosts.deny file? What to do with that? And deleting hacked system? u mean reinstall?

---

### Post by IntuitiveNipple on 2007-01-22
Just stumbled on this thread whilst looking for something else, but it made me think, where's the increase in security of not having a root account enabled?

Whether the attacker tries to log-in as root or using a regular username, its still only one password to crack, and when its a *friend* who knows your username already there's no increase in security based on the attacker not being able to guess the username to try.

Once they've obtained the password to that user account (maybe brute-forced that account with a dictionary attack as sounds likely in this case) they can use "sudo su" to gain super-user privileges in most cases.

If they get unsupervised access to the machine for only a few seconds (left logged in and unattended) they can easily copy the password file and then attempt to crack it at their leisure on another PC.

Or have I missed something fundamental here?

---

### Post by meng on 2007-01-22
> **r0ck80y said:**
> he wont reveal the trick to me unless i treat him with a king-size chicken burger. :biggrin:
Maybe you should "hack" his chickenburger.
(By the way, I don't condone hacking chickenburgers.)

---

### Post by ~LoKe on 2007-01-22
I think you just had a weak password.  Change it to something cryptic, like: **gt6^tre!112_%**
And ask him to try it again.

---

### Post by ardchoille42 on 2007-01-22
> **Hossie said:**
> Why is Ubuntu more safe? If you hack the normal account, you can use as much sudo as you like and thus "are root"? Where is the enhanced security? In guessing the username? :o

How are you going to hack the normal accounts on my computer when you don't know the usernames of the accounts to hack? Not only that, but I have set sudo to ask for the root password ever time, not using a "timeout" feature - that feature is insecure in my opinion. If you did hack into my user account, you can't run sudo. And I have protected the /bin/su command so that all users not in the wheel group simply get a "permission denied" error when running "su", so they can't sit there and run su repeatedly to try to guess the root password.

You can protect the su command with:

```

sudo addgroup wheel
sudo adduser USERNAME wheel
sudo chown root:wheel /bin/su
sudo chmod 4750 /bin/su

```

Computer security is a continual process, not a destination.

---

### Post by ardchoille42 on 2007-01-22
> **IntuitiveNipple said:**
> Just stumbled on this thread whilst looking for something else, but it made me think, where's the increase in security of not having a root account enabled?

Whether the attacker tries to log-in as root or using a regular username, its still only one password to crack, and when its a *friend* who knows your username already there's no increase in security based on the attacker not being able to guess the username to try.

Once they've obtained the password to that user account (maybe brute-forced that account with a dictionary attack as sounds likely in this case) they can use "sudo su" to gain super-user privileges in most cases.

If they get unsupervised access to the machine for only a few seconds (left logged in and unattended) they can easily copy the password file and then attempt to crack it at their leisure on another PC.

Or have I missed something fundamental here?

In order to hack the root account, that account needs to be enabled. The root account is disabled in Ubuntu by default, and for good reason.

In order to hack into a user account, you need to know the user names/user accounts to hack into. Do you know the user accounts on my computer? No, so you can't hack into them since you don't know what to hack into.

If the root account is enabled, then a person can sit and try to hack into it all day long.

This is one of the many things that makes Ubuntu the best Linux distro on the planet :)

---

### Post by r0ck80y on 2007-01-22
> **~LoKe said:**
> I think you just had a weak password.  Change it to something cryptic, like: **gt6^tre!112_%**
And ask him to try it again.

Okie, will do that and test him tomm but yeah, as IntuitiveNipple pointed out, wheres the increased security?? I'll read that link ardchoille42 submitted later...

And also he did talk to me about "john the ripper" some days ago...but i doubt if he used that  coz i dont keep my comp running all day...ummm...i dunno..am jus speculating things here..*sigh*

---

### Post by r0ck80y on 2007-01-22
> **ardchoille42 said:**
> 
If the root account is enabled, then a person can sit and try to hack into it all day long.


I see the point here.."root" is one of the standard users on every linux system and the root user is called just that..."root" ( not "rwoot" as elmer fudd would say :p  )

---

### Post by ardchoille42 on 2007-01-22
> **r0ck80y said:**
> Okie, will do that and test him tomm but yeah, as IntuitiveNipple pointed out, wheres the increased security?? I'll read that link ardchoille42 submitted later...

And also he did talk to me about "john the ripper" some days ago...but i doubt if he used that  coz i dont keep my comp running all day...ummm...i dunno..am jus speculating things here..*sigh*

I think john the ripper uses a dictionary-type attack. That probably won't work with a strong password. I tried john the ripper when I used Windows some time ago and, from a security standpoint, it isn't as great as everyone thinks it is. I also recommend changing your password weekly.. that should throw a wrench into john the ripper's works ;)

---

### Post by Daveski on 2007-01-22
> **Hossie said:**
> Why is Ubuntu more safe? If you hack the normal account, you can use as much sudo as you like and thus "are root"? Where is the enhanced security? In guessing the username? :o

My understanding is that you are correct - if someone hacks your user account and so knows your password, they do indeed have the right to sudo anything by default. I think the added security is that automated processes such as viruses, trojans and other malicious software will usually be running as the user and not sudo'ed with root privs.

---

### Post by Enverex on 2007-01-22
My guess is that the "enhanced security" is in the name. Sure that point is moot if someone knows your login, but most attacks are bots trying to gain access to machines via root or other standard names, which means they'll never even know the right username to try and log-in against.

But I agree with the others, you most likely just had a crappy password and he guessed it, that or he saw you type it at some point. You can't just "decode" the password.

---

### Post by r0ck80y on 2007-01-22
:frown: 
I have a BIG problem now!!! ROOT DOES NOT EXIST !!!!
I didnt mention that when i was having the discussion with my friend i tried to challenge him to crack the new root pass again and then i changed the perms of passwd/shadow file to 000 ( yeah, i am a moron ](*,)  ) but then after running a few other commands i restored the perms. Just a few mins ago i tried to open a new shell (xfce4-terminal) and it says :
```

Failed to execute child

Unable to determine your login shell.
Please check your system setup.
```

Konsole opens with :```

I have no name!@r0ck80y:~$
```

Open synaptic or adept thru kde menu ---> well nothing happens
Logging in thru kde now shows a new error "fatal sound error: cannot create mcop dir..."

Aahh!! This is painful...forgive my foolishness if i have done something wrong but plz HAALP!!!

---

### Post by Sef on 2007-01-22
The other possibility is that he has installed a keylogger on your system.   I would do a clean install and then reset the password as suggested by ~Loke.

---

### Post by r0ck80y on 2007-01-22
I have a BIG problem now!!! ROOT DOES NOT EXIST !!!!
I didnt mention that when i was having the discussion with my friend i tried to challenge him to crack the new root pass again and then i changed the perms of passwd/shadow file to 000 ( yeah, i am a moron ) but then after running a few other commands i restored the perms. Just a few mins ago i tried to open a new shell (xfce4-terminal) and it says :
```


Failed to execute child Unable to determine your login shell. Please check your system setup. 
```

Konsole opens with :
```


I have no name!@r0ck80y:~$
```

Open synaptic or adept thru kde menu ---> well nothing happens
Logging in thru kde now shows a new error "fatal sound error: cannot create mcop dir..."
I was able to do sudo apt-get install passwd but still no effect.....

Aahh!! This is painful...forgive my foolishness if i have done something wrong but plz HAALP!!!

---

### Post by kbudurka on 2007-01-22
First thing that is good is that "root" is not a valid login.
But also, only your FIRST username in ubuntu is able to use "sudo" by default.
So if you set up an account for your friend "jim", jim can not do things like:
sudo gedit /etc/sudoers

Only your first username can do that. You would need to add "jim" to the /etc/sudoers file to grant him/her similar permissions.

---

### Post by r0ck80y on 2007-01-23
Just read my last thread again...
its happening in suse as well..i open konsole and the prompt reads :
```

cannot find user w/ uid 500
id: cannot find name for user ID 500

I have no name!@r0ck80y:~$
I have no name!@r0ck80y:~$
```

and i hadnt touched the suse passwd files at all. When i type, say, adept or yast at this prompt, it says "kdesu: ERROR: User root does not exist". :confused:  ](*,)

---

### Post by Enverex on 2007-01-23
He's hosed your PC. I recommend beating him up, getting some new friends and not letting them access your PCs when you have such easy logins.

---

### Post by r0ck80y on 2007-01-23
> **Enverex said:**
> He's hosed your PC. I recommend beating him up, getting some new friends and not letting them access your PCs when you have such easy logins.

Oh I'll beat him up alright !! :mad:   
But *sigh* cant something be done now to recover ? Should i reinstall? Is that final?

---

### Post by bernied on 2007-01-23
> **Enverex said:**
> He's hosed your PC. I recommend beating him up, getting some new friends and not letting them access your PCs when you have such easy logins.
I agree, and he can just forget about that chicken-burger. If he hasn't hosed it, you have. A new install is probably easiest at this point.

I don't agree that he's not a friend, better that he taught you that lesson than someone else.

You can still get any important files you might need off the machine using a live-cd - but don't  keep any executables or configuration files unless you are really sure.

You will find enlightenment in paranoia.

---

### Post by bernied on 2007-01-23
> **r0ck80y said:**
> Oh I'll beat him up alright !! :mad:   
But *sigh* cant something be done now to recover ? Should i reinstall? Is that final?
Unless you know exactly what he (and you) has done, you won't know if you have recovered, even if you get things 'back to normal'. How much do you trust him?

---

### Post by lyceum on 2007-01-23
I would put a freash install on it and see if he can do it again. Don't give him any time either, it it takes him a week, then he is scaming you. IF he can do it again easily, I would really like to see the how-to.

---

### Post by r0ck80y on 2007-01-23
> **lyceum said:**
> I would put a freash install on it and see if he can do it again. Don't give him any time either, it it takes him a week, then he is scaming you. IF he can do it again easily, I would really like to see the how-to.

The missing root user is taken care of...i changed the perms on shadow (640) and passwd (664)

That fellow says he will tell me what he did..." be patient, i am just testing my skills" ; that wily son of a *****
Anyways, I asked him if he can chg the new pass now, to which he replied that he cant really say for sure.
So what happened could be a pure hack or a simple breach due to bad security mgmt on my part, either way i'll find out soon ( i wont rest till i do ) and shall post here again....

Thanx for all the help guys !!! :)

---

