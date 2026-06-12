---
title: "Are immutable, root owned files under a user's home folder safe?"
date: 2014-07-26
forum: General Help
---

### Post by terminator14 on 2014-07-26
If I wanted to leave a script in /home/$USER/bin/, and occasionally run the script by $USER AND root, what's a safe way to do this?
Yes - the script should really be in a place like /bin or /usr/bin, where the regular users can't write to it, and it's safe, but let's forget about that for a minute and assume I need it in /home/$USER/bin.

What I want to know is - does this make sense, or am I missing something:

If you have a script in /home/$USER/bin that root will at some point need to run, there are several security problems that need to be addressed:

[LIST]
[*]If $USER can edit the file, he can add arbitrary code to the script and wait for root to run it with root privileges
[INDENT]Solution: $ sudo chown root:root script.sh; sudo chmod 755 script.sh[/INDENT]
[*]Even if $USER can't write to the file (because of the previous solution), they can delete it. This means they can copy the contents of the original script, delete the script, create a new script in its place, paste the contents of the original into it, and add arbitrary code to the new file. Unless the root user notices that the file is no longer owned by root:root (which is unlikely - who checks the ownership of a file before executing it?) or the fact that there's changes in it (who reads every line of a script every time they want to run it?), root will run the script with the user's "additional" code
[INDENT]Solution: $ sudo chattr +i script.sh
This prevents the user from deleting the file, or its parent folders[/INDENT]
[/LIST]
Does this, in theory, make the script safe to leave in the user's home directory (even if it is bad practice)?

---

### Post by Tadaen_Sylvermane on 2014-07-26
Theoretically yes. Seems like a bunch of trouble to go through and the only result is putting a script or executable in the wrong place. I would love to know the reason for this line of thought as this seems to be a not to bright way to do something.

---

### Post by terminator14 on 2014-07-26
I write many small scripts, and I don't always remember their names. Finding a script I wrote 6 months ago somewhere in /bin/ among 100 other scripts/binaries is impossible
Finding it in ~/bin/ is easy.
I am $USER, but sometimes those scripts need to be run as root (with sudo), which is easy to do, but not entirely secure if my $USER account ever gets compromised, for the reasons mentioned earlier.

My choices are:
[LIST]
[*]Make the scripts owned by root, 755, and immutable, and store it in /home/$USER/bin
			**Advantages**: Easy to do
			**Disadvantages**: Must remove -i flag every time you want to change the script, and remember to add it again when done editing
			**Notes**: Good option only if the script rarely needs to be changed

		OR


[*]Put the script into /bin and make a symlink to the script in /home/$USER/bin/
			**Advantages**: Don't need to clear immutable attribute every time you want to edit the file
			**Disadvantages**: Initial setup (moving to /bin/, creating symlinks) takes slightly longer. Not a big deal for one or two scripts, but convincing yourself to do this every time you start a new script can be a challenge.
**Notes**: Good option if the script needs to be changed often
[/LIST]

---

### Post by steeldriver on 2014-07-26
... sounds like the perfect use-case for /usr/local/bin/

---

### Post by Tadaen_Sylvermane on 2014-07-26
I do it the other way although I admittedly don't use many scripts. I keep the script in my /home/$USER/bin and create a link in /bin. I don't know if that is appropriate just that it hasn't caused me a touch of trouble yet. I chown the scripts to root:$USER and give  myself 764 permissions for script I only want to run as root. No trouble for editing and can only be executed as root.

It sounds like you want to lock yourself out of the script for editing? Or is the same user account being shared with others. If that's the case then utilizing the multi-user nature of linux is the better choice than working around the security.

> **Disadvantages: Initial setup (moving to /bin/, creating symlinks) takes slightly longer. Not a big deal for one or two scripts, but convincing yourself to do this every time you start a new script can be a challenge.**

Write a script that creates a template script in the proper places, proper permissions and creates a link in whichever bin you want it. Run as sudo. Maybe something like this?

```
#!/bin/bash

##### begin script #####
main() {
  createscript() {
    # create template script
    echo "#!/bin/bash
# Author - Tadaen Sylvermane
# Creation date -
# Last edit -


##### variables #####


##### begin script #####


##### end script #####" > $1


    #set permissions and create link
    chmod 764 "$1"
    chown "root:$2" "$1"
    cd /bin && ln -s "$1"


    # close it out
    clear && read -p "Script template created. Begin editing? ( y/n )" templateopt0
    if [[ "$templateopt0" == [Yy] ]] ; then
      # whatever your editor is
      vi $1
    else
      echo "Don't forget to edit the script!"
    fi
  }
  createscript $1 $2
}


main "$1" "$2"


##### end script #####

```

I made it a function to make it easier with sudo, remove it from function if you can run as root itself.

---

### Post by terminator14 on 2014-07-26
> **Tadaen_Sylvermane said:**
> I do it the other way although I admittedly don't use many scripts. I keep the script in my /home/$USER/bin and create a link in /bin. I don't know if that is appropriate just that it hasn't caused me a touch of trouble yet. I chown the scripts to root:$USER and give  myself 764 permissions for script I only want to run as root. No trouble for editing and can only be executed as root.



This makes the script editable by $USER, and runable by root, which means if the $USER account is ever compromised, all an attacker has to do to get root privileges is use the $USER account to write an extra couple of lines in that script that either creates a new admin user, or elevates $USER to admin (in theory it's as easy as adding the user to the sudo group, which is one line), and wait until root runs the script. It's a lot easier to gain access to a regular user account for a hacker than the root account (SSH disallows root logins by default, most programs you download run as regular user, etc.), so this basically makes the root account only slightly harder to hack than a regular user. 

I've never had problems keeping my scripts in /home/$USER/bin either - I just recognize the security vulnerability, and sometimes it worries me.


> **Tadaen_Sylvermane said:**
> 
It sounds like you want to lock yourself out of the script for editing? Or is the same user account being shared with others. If that's the case then utilizing the multi-user nature of linux is the better choice than working around the security.

Write a script that creates a template script in the proper places, proper permissions and creates a link in whichever bin you want it. Run as sudo. Maybe something like this?

```
Script
```

I made it a function to make it easier with sudo, remove it from function if you can run as root itself.

A script to create scripts. I like it. I also like how organized your template is. Thanks

---

### Post by terminator14 on 2014-07-26
> **steeldriver said:**
> ... sounds like the perfect use-case for /usr/local/bin/

I think that's what I've been missing. Easy to get to ("cd /usr/local/bin" is fairly short), not cluttered, already part of everyone's $PATH in most cases, owned by root (so the folder can't be deleted and replaced by regular users).
Awesome! Thanks!

Note for anyone else trying this: If the scripts you put in /usr/local/bin can run as root, and as regular user, but not with sudo (eg. "$ sudo script.sh" shows "script.sh not found"), it might be because sudo has a completely different $PATH than both the user you run it as and root. Sudo's $PATH can be set in /etc/sudoers. Just search the file for 'secure_path'

---

