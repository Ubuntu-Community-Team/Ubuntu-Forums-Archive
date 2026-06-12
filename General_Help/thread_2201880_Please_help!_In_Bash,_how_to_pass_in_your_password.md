---
title: "Please help! In Bash, how to pass in your password without promting"
date: 2014-01-26
forum: General Help
---

### Post by fredyfontaine on 2014-01-26
Hello and thanks for reading my post.
Sorry if this has already been asking but I can't find the answer to my question anywhere.
I would like my Bash script to ask a user for their password, save it as a variable and then every time Ubuntu needs the password it automatically adds in the variable. 

For example my script is :

[COLOR=#000080]#!/bin/bash
read -s -p "Password: " mypassword

sudo apt-get --purge remove apache

[/COLOR][COLOR=#ff0000]password = mypassword(this is obviously wrong)[/COLOR][COLOR=#000080]

exit 0[/COLOR]

I realise this is probably not good security practice but it's just for a college project so it doesn't really matter. I'm a total newbie so please be gentle with the explanations! Please assume I don't know anything - you won't be insulting my intelligence!
Many thanks,
Brian

---

### Post by Lars Noodén on 2014-01-26
I've seen scripts that used [expect](http://manpages.ubuntu.com/manpages/trusty/en/man1/expect.1.html) to pass login and other info, but haven't used it myself.  It's a common word, making it harder to find in the search engines,  but if you look you should be able to find HowTos or tutorials.

---

### Post by steeldriver on 2014-01-26
Hello and welcome to the forums

IMHO college should be a place where you learn to do things the right way :)

Since sudo already prompts for the user's password, and "saves" the authorization for a configurable amount of time (by default it is 15mins I think) I don't see the point of saving the actual password. If that's not sufficient then a better solution would be to create a group of users who are allowed to execute the apt-get command without a password, and configure the sudoers file accordingly.

If you still want to go ahead with saving and reusing the password - read the man page (in particular the -S option).

---

### Post by fredyfontaine on 2014-01-26
Thanks for your help Lars. I'll see if I can run an Expect script inside a Bash script (there's a lot more Bash code so I need it to be in bash)

---

### Post by fredyfontaine on 2014-01-26
Thanks for your help SteelDriver! The problem is a long script where things like mysql and Apache get installed and I don't think I can do it on a user level because the script has to be able to be run on any server. In other words, I give you the script and it works for you if that makes sense.
Thanks again

---

### Post by fredyfontaine on 2014-01-26
Just an update - I think it might be OK if I just forget about asking for passwords and run the scripts as sudo, as in:
 sudo ./script.sh

---

