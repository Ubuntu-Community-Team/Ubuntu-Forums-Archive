---
title: "Software Center problem"
date: 2013-08-17
forum: General Help
---

### Post by jaspenhof2 on 2013-08-17
Every time I try to install a new program, I get the warning that it "Requires installation of untrusted packages".  No matter whether I click on Repair or OK, it pops up again and again and I can't install anything.
Thanks for your time.
Spence

---

### Post by ibjsb4 on 2013-08-17
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

And please post the output.

---

### Post by newbie-user on 2013-08-17
You may need to add the key for any non-standard repositories you might have added. For example: 
```
apt-key adv --recv-key --keyserver keyserver.ubuntu.com A040830F7FAC5991
```

---

### Post by jaspenhof2 on 2013-08-18
[ 						 							]("http://ubuntuforums.org/member.php?u=1729120")[**[COLOR=#000000]ibjsb4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1729120")  Thanks.  I tried that but it didn't solve the problem.  I'm now updated though.

**Newbie user**  Thanks.  Is that code exactly what I need to enter into the Terminal?

---

### Post by Bashing-om on 2013-08-18
jaspenhof2; Hi !

I expect that the key code will be different...
run in terminal:
```

sudo apt-get update
sudo apt-get upgrade

```
I expect that in the out put of the "upgrade" command to have "W: GPG error:"
Substitute that public key(s) -one at a time - into the above command sequence.


[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by jaspenhof2 on 2013-08-18
**Bashing-om**  I ran both of those sudos and yes, there was a "W:GPG error:" but I lost you at that point.  I'm almost totally lost on this.  Thanks for your time.

---

### Post by ibjsb4 on 2013-08-18
apt-key adv --recv-key --keyserver keyserver.ubuntu.com [COLOR=#ff0000]A040830F7FAC5991[/COLOR]

Replace the red highlighted with the correct one associated with the gpg error.

Edit:  and yes, enter that in terminal

---

### Post by jaspenhof2 on 2013-08-18
**ibjsb4** Thanks !  I'll do that shortly. Thanks for your help

---

### Post by jaspenhof2 on 2013-08-18
[FONT=Verdana, Arial, Helvetica][SIZE=2][B]Tried the above.  Still getting the error.  Here's what I'm getting at the end of the update:

W:  a error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error:  [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release:  The following signatures were invalid:  BADSIG 16126D3A3E5C1192  Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W:  GPG error:  [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release:  The following signatures were invalid:  BADSIG 40976EAF437D05B5  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W:  Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/Release](http://extras.ubuntu.com/ubuntu/dists/raring/Release)

W:  Some index files failed to download.  They have been ignored, or old ones used instead.

Thanks again.
[/B][/SIZE][/FONT]

---

### Post by Bashing-om on 2013-08-18
jaspenhof2; Hey ..
You are doing in terminal ???
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5

```
presactly ????

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by jaspenhof2 on 2013-08-18
Yes, in terminal and  I will input those lines shortly
Thanks

---

### Post by jaspenhof2 on 2013-08-18
The 2nd line went in okay with no problems.
The 1st line was rejected: gpg: "16126D3A3ESC1192" not a key ID: skipping

---

### Post by jaspenhof2 on 2013-08-18
The 2nd line went in okay, with no problem.
The 1st line was rejected: 
gpg:  "16126D3A3ESC1192" not a key ID: skipping

---

### Post by Bashing-om on 2013-08-18
jaspenhof2' Well ...

gpg: "16126D3A3ESC1192" not a key ID: skipping
        16126D3A3E5C1192
        16126D3A3E5C1192
All agree with the intitial key ... humm..
run 
```

sudo apt-get upgrade

``` once more and verify the authorization key it is requesting.

else going to have to go deeper.

---

### Post by jaspenhof2 on 2013-08-18
Now it's saying that both of those IDs are "invalid" but there's no indication of what they should be.

---

### Post by Bashing-om on 2013-08-18
jaspenhof2; Well... well;

Try to run the following comamnd from terminal
```

sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update

```
when we do not know ...acquire them all./

[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by jaspenhof2 on 2013-08-18
Came back with 

sudo: aptitude: command not found

I'm gonna get some sleep.  I'll check in tomorrow.  Thanks for your help and patience.

---

### Post by Bashing-om on 2013-08-18
jaspenhof2; Yeh ..

A slip of mind ... on my part .. the utility "aptitude" is no longer installed by default ..

When ya return ... post back a fresh output with the updated errors from :
```

sudo apt-get upgrade

``` see what I can come up with.

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by jaspenhof2 on 2013-08-19
Tried to "upgrade" and it came back there was nothing to upgrade.  Trying the "update" now
"W: A error occurred during the signature verification.  The repository is not updated and the previous indes files will be used.  GPG error:  [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release:  The following signatures were invalid:  BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Sining Key <ftpmaster@ubuntu.com>"

"W GPG error:  [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring release:  The following signatures were invalid:  BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Singing Key<ftpmaster@ubuntu.com>"

---

### Post by Bashing-om on 2013-08-19
jaspenhof2; Hey ..
Let's assume the data base is corrupted .. run these in terminal, one command at a time.
```

sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

```
and advise on the result.
[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by jaspenhof2 on 2013-08-19
Results:
GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release:: The following signatures were invalid: BADSIG 16126D3A3E5C1192
GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring  Release: The following signatures were invalid: BADSIG 40976EAF437D05B5

We keep putting in those same signatures and they keep getting rejected.  Any way of finding out what they're looking for?

---

### Post by Bashing-om on 2013-08-19
jaspenhof2; Sheesshh ..
Ok try this approach:
```

sudo gpg --keyserver keyserver.ubuntu.com --recv-key 16126D3A3E5C1192
sudo gpg -a --export 16126D3A3E5C1192 | sudo apt-key add -

```
see if that will update your database.
Which does in 2 steps what the former command should have done in 1 step.
[INDENT]else I will really have to put on my think'n cap !
[/INDENT]

---

### Post by jaspenhof2 on 2013-08-19
Results:

jaspenhof@jaspenhof-ThinkPad:~$ sudo gpg --keyserver keyserver.ubuntu.com --recv-key 16126D3A3E5C1192
gpg: WARNING: unsafe ownership on configuration file `/home/jaspenhof/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
jaspenhof@jaspenhof-ThinkPad:~$ sudo gpg -a --export 16126D3A3E5C1192 | sudo apt-key add -
gpg: WARNING: unsafe ownership on configuration file `/home/jaspenhof/.gnupg/gpg.conf'
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.

---

### Post by Bashing-om on 2013-08-19
jaspenhof2; Well !

Let's just see about that ... maybe a hint in the right direction.
```

ls -la /home/jaspenhof/.gnupg/gpg.conf

```
and we will see what the permissions on the file are.

[INDENT][INDENT]we want to know
[/INDENT][/INDENT]

---

### Post by jaspenhof2 on 2013-08-19
Results

jaspenhof@jaspenhof-ThinkPad:~$ ls -la /home/jaspenhof/.gnupg/gpg.conf
-rw------- 1 jaspenhof jaspenhof 9398 Jun 20 08:09 /home/jaspenhof/.gnupg/gpg.conf

---

### Post by Bashing-om on 2013-08-19
jaspenhof2; Humm..
Those permissions are correct ...presently I am at a loss .. lemme go see what I can find out about this. When I do not know .. I want to find out !

[INDENT][INDENT]I'll be back
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-08-19
jaspenhof2; I AM back ..

Verify prior to initiating this solution:
a) You are not behind a firewall,
b) There is no "proxy" in your network that you are going through.

Then:
Try deleting the key:
```

sudo apt-key del 16126D3A3E5C1192

```
then updating the repository
```

sudo apt-get update

```
NOW -> You should get a NO_PUBKEY error instead of a BADSIG error and
```

sudo apt-key finger

```
should not find the key (called "Ubuntu Extras Archive Automatic Signing Key")

Now add the key back again;
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192

```
The result of apt-key finger should have
pub   1024D/3E5C1192 2010-09-20
      Key fingerprint = C474 15DF F48C 0964 5B78  6094 1612 6D3A 3E5C 1192
uid                  Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

If this is successful........ repeat for the other key.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by jaspenhof2 on 2013-08-19
It seemed to go well.  Here's the result of that maneuver.

jaspenhof@jaspenhof-ThinkPad:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.axWG3yaz3w --trustdb-name /etc/apt//trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: public key "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1

---

### Post by jaspenhof2 on 2013-08-19
Should I proceed with the 2nd signature?

---

### Post by Bashing-om on 2013-08-19
jaspenhof2; Hey ...Yes I agree that does look good.

Go ahead with the other ... substituting the proper signing key.
Looks as if the keys in the auth file were bad huh ?

[INDENT][INDENT]mov'n on and upward
[/INDENT][/INDENT]

---

### Post by jaspenhof2 on 2013-08-19
Results of 2nd signature maneuver:

jaspenhof@jaspenhof-ThinkPad:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.VaXcJ490px --trustdb-name /etc/apt//trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: public key "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1

---

### Post by Bashing-om on 2013-08-19
jaspenhof2; looks good .. 
should be set to go ! -- do:
```

sudo apt-get update
sudo apt-get upgrade

```
and advise results.

[INDENT][INDENT]ain't noth'n but a thing
[/INDENT][/INDENT]

---

### Post by jaspenhof2 on 2013-08-19
Bad news, I think.  Results of the update:
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Results of upgrade:
jaspenhof@jaspenhof-ThinkPad:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by jaspenhof2 on 2013-08-19
At what point do I throw in the towel and try a reinstall of ubuntu.  I've got an xhd that has most of my stuff on it and I can move the rest over.  I don't know if that would work though.

---

### Post by Bashing-om on 2013-08-20
jaspenhof2; That blows me away !

We have moved the data files, rebuilt the indexs;
removed the old singing keys and downloaded the correct signatures and exported them ...
And still the problem persist !

I honestly at this point do not know how to fix this situation .. getting deeper into the system than I know how to relate with.
I am more than happy to stay with you and explore this situation and try and find a solution,,, 
It will take me a while to research what the process involves and the trouble shooting steps needed to find where the process is failing ..

It is a process failing and not a system failure .. no real need to (re-)install.

(Re-)installation is the final solution ...........though it is a guaranteed fix.

I'll give this my consideration and we can await others' advisement -perhaps greater knowledge -  on this situation.

[INDENT][INDENT]time and effort cures a lot of ails 
[/INDENT][/INDENT]

---

### Post by jaspenhof2 on 2013-08-20
No need to worry.  Someone else, on the launching pad suggested the following.  It worked!

sudo apt-key adv --recv-key --keyserver keyserver.ubuntu.com 16126D3A3E5C1192
sudo apt-key adv --recv-key --keyserver keyserver.ubuntu.com 40976EAF437D05B5

Then remove the old lists

sudo rm -rf [I]/var/lib/apt/lists/*


[/I]I guess removing the old lists was the key.  Anyway, I'm able to download again and no nasty warnings.
I want to thank you for sticking with this problem and trying so hard. With all of our work, I managed to learn something and that is always a good thing.  Thanks again!  Spence

---

### Post by Bashing-om on 2013-08-20
jaspenhof2; Outstanding ! You do good work.

And I too learned something.

Please mark this thread as solved ->
Aides others seeking a solution, as well as; Helps keep the forum tidy.
Thread Tools drop-down -> Mark thread as solved.

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

