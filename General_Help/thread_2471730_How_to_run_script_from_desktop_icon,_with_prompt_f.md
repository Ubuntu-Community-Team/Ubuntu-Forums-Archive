---
title: "How to run script from desktop icon, with prompt for sudo/root?"
date: 2022-02-07
forum: General Help
---

### Post by bsh on 2022-02-07
Hey all,
I'm using a script, for which I created a convenient desktop icon. Years and years ago. It needs to run as root, or with sudo.
It was working fine many years ago, just asking for password in a popup window and go. Then IIRC there was some changes, so I had to modify the launcher to launch the script with gksu. It worked fine again, until gksu has been removed in 18.04 or something. After that I found a solution, using pkexec. It was sorta working: usually first tie launching the icon, the password popup popped up and then just disappeared and nothing happened. But trying it again usually worked.
But since I upgraded xubuntu to 20.04, now the popup vanishes all the time, so it won't run the script.
My question is, what is the correct way nowadays to run script form desktop icon, as root, prompting for password etc.?

---

### Post by MAFoElffen on 2022-02-08
Every time you preface with sudo, I will check that the current user is a part of sudoers... If in their cache and not timed out, it will not prompt... So what I do is to do this in my script at the start of
```

    if [[ "$EUID" == 0 ]]
    then 
   ...

```
I don't like to start out as a user already being root... there are things I want to run a the logged in user. I want ot make sure I know what level they are at, at the start, and where to guide them from there... I find that as being more predictable and consistent.

Then 
```

sudo -k # revoke previously cached sudo password 
        if sudo true
        then 
        ...

```
Again, revoke any cached sudo privileges, to start at a baselline, and require the User to use their password to get those previledges.

Does that make sense? Does that help with what you want to do?

For the second part of that:
```

[Desktop Entry]
Version=01.00-02
Exec=/home/mafoelffen/Scripts/system-info
Name=UbuntuForums system-info Script
GenericName=system-info
Comment=Ubuntu system support script.
Encoding=UTF-8
Terminal=true
Type=Application
Categories=Application;Network;Settings;Utility;

```

---

### Post by bsh on 2022-02-08
> **MAFoElffen said:**
> 
Does that make sense? Does that help with what you want to do?
[/code]

umm, not really. the script itself doesn't do su or sudo. it is meant to be run with root privileges already. The question is how do I do that from a desktop icon and why pkexec doesn't work, why the popup disappears...

---

### Post by MAFoElffen on 2022-02-08
> **bsh said:**
> umm, not really. the script itself doesn't do su or sudo. it is meant to be run with root privileges already. The question is how do I do that from a desktop icon and why pkexec doesn't work, why the popup disappears...

Your solution in Post #1 is still supposedly the current accepted solution. At Gnome 3.x through current, gksudo was replaced by pkexec. (Although there was recent vulnerability exploit found with that.)
Example:
```
Exec=pkexec /opt/lampp/manager-linux-x64.run 

```
Are you saying that does not work now?

Another way used to be to use sudo in the Exec line, but to do that, to make it work, you had to add the application to the sudoers file...

---

### Post by MAFoElffen on 2022-02-08
Oh Dang. It "has" Changed...

I found some recent info on pkexec and .desktop files from 2021...
[https://itectec.com/ubuntu/ubuntu-pkexec-command-in-a-desktop-file/](https://itectec.com/ubuntu/ubuntu-pkexec-command-in-a-desktop-file/)
[https://itectec.com/ubuntu/ubuntu-how-to-configure-pkexec/](https://itectec.com/ubuntu/ubuntu-how-to-configure-pkexec/)

---

### Post by bsh on 2022-02-08
> **MAFoElffen said:**
> 
Are you saying that does not work now?
Whenever I doubleclick the desktop icon to run the script, the popuc flashes (asking for the sudo password) but immediately disappears, as if it were crashing or something. It did that once before the upgrade from 18.04 to 20.04 but then it worked on a second try so I didn't bother. Butr now it never works, popup always disappears. No idea why or how to figure it out.
Oh, and it definitely doesn't work (not even a popup) over a vnc session.

---

### Post by TheFu on 2022-02-08
If it is safe to run for a specific userid, always, with elevated privileges, then you can modify the suders file to allow that exact userid to run the exact commands without a password prompt. The sudoers manpage has examples of this exact thing, along with some caveats which are important.

If this is for backups, the better solution would be to schedule it and have it run from the main system crontab (/etc/crontab) or even the root crontab (sudo crontab -e) or if you don't really care exactly when it runs, you can drop the script into the /etc/cron.daily/ directory and it will be run, at most, daily.  On most of my Ubuntu systems, anacron runs the daily tasks around 6:25 am ... if the system is on or about an hour after the system gets booted, if it isn't on.  If there are external dependencies, perhaps an external USB storage device needs to be connected and mounted, then you can have the script check for that using different techniques. I check the mount table for the expected mount, but lots of people place an empty .mounted file in the root of the mounted partition, so if that file exists, then the storage is mounted. If it doesn't then you can either mount it or kick out an error - (**wall** will interrupt everyone on the system with a message).

Lots of options.

I have never used pkexec and after the 12 yr old vulnerability was announced 2 weeks ago, I'm glad.  GUI stuff attempting to make things easier seems to bring more attack vectors and poorly created code.  There's just something about GUI code that make security 10,000x harder.

---

### Post by bsh on 2022-02-09
> **TheFu said:**
> If this is for backups
If there are external dependencies, perhaps an external USB storage device needs to be connected and mounted, then you can have the script check for that using different techniques.
it is exactly for that. backups onto external drives. I run it when I physically go to the server and attach the drive. the script checks for the drives' presence.
I'm not worried about security, I just don't get why it is so hard a convoluted to do simple tasks nowadays, in the name of security. And why is it now suddenly not working.
I don't know... But since the popup flashes in, I assume pkexec does work, but then the popup disappearing suggests some kind of a crash or similar.
Maybe this?
> polkitd(authority=local): Operator of unix-session:c5 FAILED to authenticate to gain authorization for action org.freedesktop.policykit.exec for unix-process:146406:786615 [/usr/bin/xfce4-terminal -x pkexec /etc/scripts/backup-ext] (owned by unix-user:xxxxx)

---

### Post by TheFu on 2022-02-09
There was a 12 yr old SEV-1 security bug in PolKit (aka PolicyKit) announced last week. Any user with a local account could pwn the box completely.  I don't know what they did as the fix. I don't use polkit directly, if at all. They could have just taken away the ability to su with it while they work on a better solution. IDK.
Read more here: [https://ubuntu.com/security/notices/USN-5252-1](https://ubuntu.com/security/notices/USN-5252-1)

To see which version you have:
```
$ dpkg -l policykit-1* 
```

I have and tried to use pkexec but it didn't work.  It might not work in my odd environment. I tried on multiple systems and with GUI and non-GUI programs.

My suggestion to update the sudoers file still stands.  If you have a GUI backup program, be 100% certain to use **sudo -H**. Without the -H option, bad things can happen.

---

### Post by bsh on 2022-02-10
> **TheFu said:**
> 
I have and tried to use pkexec but it didn't work.  It might not work in my odd environment. I tried on multiple systems and with GUI and non-GUI programs.

I did some very basic test: created a new launcher icon on the desktop, with this command: "pkexec xfce4-terminal" and ran it.
It showed the popup for authentication, and it didn't disappear. It worked and asked for the password. But after authenticating, nothing happened.
Then I tried and modified the launcer to "run in terminal". This time, the authentication popup showed up and disappeared immediately, as with my original problem.
All this happens through both VNC and local login.

---

### Post by TheFu on 2022-02-10
You got further than I.  There's no point to using VNC on any LAN, however.  Just use **ssh -X ** instead.  I run remote compound programs all - the - time; daily, constantly, this browser window is actually running on a different system on my LAN right now.

Again, you don't need pkexec. Just fix the sudoers to allow the exact command with the exact options to be run for that specific userid. It takes 20 seconds and this would be solved.

---

