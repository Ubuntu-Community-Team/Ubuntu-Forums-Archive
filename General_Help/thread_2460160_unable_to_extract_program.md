---
title: "unable to extract program"
date: 2021-04-03
forum: General Help
---

### Post by jencdi on 2021-04-03
[SIZE=4][SIZE=3]Ubuntu 20.04.02
Virtual box 6.1
Admin privileges

Download GO from their website to /downloads/

Ran following command

sudo -i   rm -rf /usr/local/go && tar -C /usr/local -xzf /home/johngalt/Downloads/go1.16.3.linux-amd64.tar.gz

receive these errors
1. cannot mkdir: permission deniedtar --help
2. exiting with failure status due to previous errors
[/SIZE][/SIZE]

---

### Post by Holger_Gehrke on 2021-04-03
That command is actually two commands separated by '&&' which means 'execute the following command if the previous one succeeded'. Since you're trying to extract a tar archive into a directory that belongs to root and that nobody else can write to, you need to use sudo for the tar-command too.
```

[SIZE=2]sudo rm -rf /usr/local/go && sudo tar -C /usr/local -xzf /home/johngalt/Downloads/go1.16.3.linux-amd64.tar.gz
[/SIZE]
```[SIZE=4][SIZE=3][SIZE=2]

Two more things:[/SIZE]
[LIST]
[*][SIZE=2]You might have mentioned what the program is, where you got it from and that the command you're trying to use is part of the official installation instructions, would have saved me a round trip to duckduckgo searching for the file name. Besides the programming language there's also a very well known board game of which there are multiple implementations and who knows what else might call itself 'go' ...[/SIZE] 
[*][SIZE=2]If you don't need the latest and greatest, there's a somewhat older version of go in the repositories. Search for 'golang' on packages.ubuntu.com (or use 'apt search golang'). [/SIZE] 
[/LIST]
[SIZE=2]
Holger[/SIZE]
[/SIZE][/SIZE]

---

