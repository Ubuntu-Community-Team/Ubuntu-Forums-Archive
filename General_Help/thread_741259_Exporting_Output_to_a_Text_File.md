---
title: "Exporting Output to a Text File"
date: 2008-03-31
forum: General Help
---

### Post by Muscle on 2008-03-31
I've just setup a Ubuntu 7.1 server to run some of my scanning tools. One of those tools is Unicornscan. Unicornscan is functioning properly. However, I am unable to export the output to a text file via the > and >> options. I end up with multiple write protected files such as unicorn-data.txt and unicorn-data.txt?.

I now understand why from this:

> Downsides of using sudo
Although for desktops the benefits of using sudo are great, there are possible issues which need to be noted: 
•	Redirecting the output of commands run with sudo requires a different approach. For instance consider sudo ls > /root/somefile will not work since it is the shell that tries to write to that file. You can use ls | sudo tee -a /root/somefile to append, or ls | sudo tee /root/somefile to overwrite contents. You could also pass the whole command to a shell process run under sudo to have the file written to with root permissions, such as sudo bash -c "ls > /root/somefile". 
•	In a lot of office environments the ONLY local user on a system is root. All other users are imported using NSS techniques such as nss-ldap. To setup a workstation, or fix it, in the case of a network failure where nss-ldap is broken, root is required. This tends to leave the system unusable unless cracked. An extra local user, or an enabled root password is needed here. 

Here is a sample of how I do it on BackTrack:

> unicornscan -mU -v -r50 192.168.1.1/32 > unicorn-data.txt

I've tried two ways on Ubuntu:

> sudo bash -c "unicornscan -mU -v -r50 192.168.1.1/32 > unicorn-data.txt"

or

> sudo bash -c "unicornscan -mU -v -r50 192.168.1.1/32 -l unicorn-data.txt"


I need it to function like it does on my BackTrack servers. I need Ubuntu to export the data to a single NON write protected .txt file. Does anyone know how I can accomplish this?

---

### Post by gavintlgold on 2008-03-31
Perhaps a chmod command right after?

---

### Post by gsmanners on 2008-03-31
You could try doing "sudo -i" then running the scan. Then just chmod/chown the output however you want, then "exit" back to user.

---

