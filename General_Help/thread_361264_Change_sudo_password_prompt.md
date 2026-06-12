---
title: "Change sudo password prompt"
date: 2007-02-14
forum: General Help
---

### Post by plwrenn on 2007-02-14
Could anyone help me find a way to change the sudo password prompt? I have noticed that sometime sudo password will be cached and it will not prompt for it. This can sometimes be confusing when running a command that also prompts for password like smbmount b/c I do not know if it is asking for smb or sudo passwrd. I would ideally like to change sudo password prompt from "Password:" to "sudo Password:".

Note: I have found many posts about disabling sudo password prompt (not secure). I do not want to do that.

---

### Post by nereid on 2007-02-14
I'm not sure that you can change the prompt and I think that it is hardcoded. But this would be a rather trivial change and you could change the prompt in the source and recompile sudo with the new prompt.

---

### Post by plwrenn on 2007-02-14
good idea. I will try that as soon as I confirm that the prompt is indeed hard coded. 

only reason I was thinking that it was not is that other distros, namely suse, have a different sudo password prompt. guess that could have made that change before they compiled it too, in which case you are absolutely correct.

thanks for the amazingly quick reply!

---

### Post by plwrenn on 2007-02-14
Ok got it. You can make an edit to /etc/sudoers file.

If you have a default configuration you should have a line something like this:

Defaults	!lecture,tty_tickets,!fqdn

Change it to something like this and save:

Defaults	!lecture,tty_tickets,!fqdn,passprompt="Enter %u's password:"

---

### Post by M$LOL on 2007-02-14
How about sudo sh to get to a prompt where you don't need sudo?

---

