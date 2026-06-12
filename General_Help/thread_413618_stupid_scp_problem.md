---
title: "stupid scp problem"
date: 2007-04-19
forum: General Help
---

### Post by Tadhg on 2007-04-19
Hopefully someone here can put me on the right track with this stupid scp problem

I have two computers at home, one is a webserver and is set up with DNS. THe other is hidden directly from the internet, but has SSH.

So I want to copy a file from the hidden computer to the web server from outside my house. Easy peasy.

So I ssh into my webserver, and from there I ssh into the hidden computer, Then I go to the folder where the file is and...

$ scp ./filename.txt timmy@192.168.0.5:/home/timmy -P 12345

(where 192,168,0,5 is the ip for the webserver)

so, should this not copy the file for me? I don't get any output. Nothing happens, no error or anything. What am I doing stupidly wrong?

---

### Post by stylishpants on 2007-04-19
The -P option must go before your file arguments.

fraser@ged:/tmp$ scp --help
usage: scp [-1246BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file]
           [-l limit] [-o ssh_option] [-P port] [-S program]
           [[user@]host1:]file1 [...] [[user@]host2:]file2

---

### Post by Tadhg on 2007-04-19
Ah! I love you!

Thanks for that. I'll have to learn to RTFM.

---

