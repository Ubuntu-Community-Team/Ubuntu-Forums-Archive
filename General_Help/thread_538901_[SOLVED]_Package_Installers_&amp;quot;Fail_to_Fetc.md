---
title: "[SOLVED] Package Installers &amp;quot;Fail to Fetch&amp;quot; Files (Ubuntu 7.0.4)"
date: 2007-08-30
forum: General Help
---

### Post by snorkytheweasel on 2007-08-30
I'm trying to use aptitude (from the terminal) and synaptic (from Gnome) to install programs (in this case, VLC Media Player).

Using either package manager, the installation fails immediately and throws this error message:

'W: Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...7.4-7_i386.deb](http://archive.ubuntu.com/ubuntu/poo...7.4-7_i386.deb)
Could not resolve "10.1.1.3:3128" '

Interestingly, I can fetch the file [http://archive.ubuntu.com/ubuntu/poo...7.4-7_i386.deb](http://archive.ubuntu.com/ubuntu/poo...7.4-7_i386.deb) if I use the address bar in Firefox.

I infer that the package managers cannot get past the proxy server - which IS 10.1.1.3 port 3128.

"Ah-ha!" I said to myself. "While Firefox reads its own configuration file to deal with the proxy, synaptic and aptitude do not use their own configuration files. They must be reading a system-wide configuration file."

Then I added, "Self (I call myself 'Self'), you'll have to configure the system-wide proxy settings using System -> Preferences -> Network Proxy"

So Self (that would be I) tried to do so. The configuration panel says that the proxy for http is "10.1.1.3:3128" ***AND*** that the port is "3128".  "10.1.1.3:3128" is probably grammatically incorrect in this context. Hence the error condition when package managers try to do their jobs.

The bad news is that when I attempt to correct my OOPSIE! using System -> Preferences -> Network Proxy, I get this error:

'The application "gnome-network-preferences" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application.'

For most, if not all, other restricted actions, Ubuntu prompts me for the password required for performing administrative tasks. Since I know both the password (I created it) AND the secret handshake, I should be able to perform this fix. In this case, the password prompt never appears. Knowing the password (and secret handshake), and being ready to use them, doesn't mean anything.

Note: I tried the old Windows do-it-all tactic: rebooting. That didn't help.

The quandry:

   1. Gnome blocks me from making needed changes
   2. Gnome doesn't ask for a password to enable making those changes
   3. Gnome won't let me use sudo to make the changes
   4. Gnome won't let me log on as root
   5. Gnome won't let me change to root

Note the interesting quirk in this: clearly, I configured that proxy setting - incorrectly - at some point in time. At that time

    * I must have assumed that "10.1.1.3:3128" was the correct syntax... in some applications that ***IS*** a syntactally correct statement (probably something in our old nemesis, Windows)
    * Gnome must have allowed me to do said configuration

Now what do I (aka 'Self') do? I'm quite content to do this from the Command Line Interface, if that's what it takes.

PS: this smells like a bug, nicht wahr?

If so, whose bug is it? Gnome? Ubuntu?

Thanks in advance, and have a great August  :)

---

### Post by bmorency on 2007-08-30
open up the file /etc/dhcp3/dhclient.conf

check to see if you have anything specified for a proxy server.
 if you do just comment it out with a #

then bring down your network card and than back up to get another ip address.

if you don't know how to bring down and back up again try this:

```
sudo ifdown eth0
sudo ifup eth0
```

---

### Post by snorkytheweasel on 2007-08-30
/etc/dhcp3/dhclient.conf

has no references to a proxy server.

I guess I'm missing something, but this ol' noob thinks he is really trying to figure out how to correct an invalid proxy configuration. If I'm wrong, well, it's neither the first mistake nor the last mistake on my rèsumè.

---

### Post by bmorency on 2007-08-30
how about checking the file /etc/profile

some system settings are in there. you are looking for a variable called "http_proxy"

try typing this at the prompt.

```
export http_proxy=""
```  and try to run aptitude

hopefully that will clear it. if not try to put this

http_proxy=""

in your /etc/profile

---

