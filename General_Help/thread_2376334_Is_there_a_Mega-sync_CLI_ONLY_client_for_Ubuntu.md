---
title: "Is there a Mega-sync CLI ONLY client for Ubuntu?"
date: 2017-11-01
forum: General Help
---

### Post by Cool_Javelin on 2017-11-01
I have installed MegaTools, and that works as advertised, but it doesn't have an automated "sync" capability.

I found the Mega GUI version, but I do not have the needed libraries it wants.

Two machines, 12.04, and 16.04, neither have GUI interface.

The ideal solution will be a CLI Mega-sync client, Next might be a freeware front end I may be able to modify some code, last I guess, I may have to 'roll-my-own'.

Thanks for any help.

Mark.

---

### Post by again? on 2017-11-02
Mega has a megacmd application.
Does that do what you want?
[https://mega.nz/cmd](https://mega.nz/cmd)
> MEGAcmd is an interactive, text console based, scriptable MEGA client. 

---

### Post by Impavidus on 2017-11-03
> **Cool_Javelin said:**
> 
Two machines, 12.04, and 16.04, neither have GUI interface.


Note that 12.04 reached end of life and should no longer be used.

---

### Post by Cool_Javelin on 2017-11-03
Thanks, guber2:

This is EXACTLY what I was looking for.
I installed it, and it seems to work as advertised.

Thanks again, Mark.

---

### Post by mikelodeon13 on 2018-03-15
> **Cool_Javelin said:**
> Thanks, guber2:

This is EXACTLY what I was looking for.
I installed it, and it seems to work as advertised.

Thanks again, Mark.

Hello Cool_Javelin,

Do you have a tutorial or what were the steps to install MEGAcmd. I have a VPS with Ubuntu 16.04 and would like to install it under CLI. Can you help me out??

Thanks.....

---

### Post by again? on 2018-03-16
Do you mean install via command line?
```
**cd** ~/Downloads && wget https://mega.nz/linux/MEGAsync/xUbuntu_16.04/amd64/megacmd-xUbuntu_16.04_amd64.deb
sudo apt install ./megacmd-xUbuntu_16.04_amd64.deb
```
You can **cd** to any directory you like prior to downloading, but when using apt to install you must use the path to the deb even when in the same directory as the deb.
Unlike dpkg, apt will resolve dependencies.

---

### Post by mikelodeon13 on 2018-03-16
Thanks for your reply.
I tried that but it seems that it is not installed or something is happening. I'm checking instructions on how to run the command but had no luck. In case you know of a tutorial, can you please share it??

Thanks again....

---

### Post by again? on 2018-03-16
Did you install with apt or dpkg?
What does this show?
```
apt policy megacmd
```

I only use the megasync GUI client but I installed megacmd to have a look.
```
**[COLOR="#006400"]glen@Xubarty:~$[/COLOR] mega-help**
/usr/bin/mega-help: /usr/share/bashdb/bashdb-main.inc: No such file or directory
/usr/bin/mega-help: warning: cannot start debugger; debugging mode disabled
Here is the list of available commands and their usage
Use "help -f" to get a brief description of the commands
You can get further help on a specific command with "command" --help 
Alternatively, you can use "help" -ff to get a complete description of all commands
Use "help --non-interactive" to learn how to use MEGAcmd with scripts
Use "help --upgrade" to learn about the limitations and obtaining PRO accounts

Commands:
      attr                import                    put
      backup              invite                    pwd
      cd                  ipc                       quit
      clear               killsession               reload
      completion          lcd                       rm
      confirm             log                       session
      cp                  login                     share
      debug               logout                    showpcr
      deleteversions      lpwd                      signup
      du                  ls                        speedlimit
      exclude             masterkey                 sync
      exit                mkdir                     thumbnail
      export              mount                     transfers
      find                mv                        userattr
      get                 passwd                    users
      help                permissions               version
      https               preview                   whoami

Verbosity: You can increase the amount of information given by any command by passing "-v" ("-vv", "-vvv", ...)
```

For more complete description run
```
mega-help -ff
```

You can get info on individual commands with mega-[COLOR="#696969"]<command>[/COLOR] --help
eg
```
mega-[COLOR="#696969"]attr[/COLOR] --help
```
Also see-----> [https://github.com/meganz/megacmd](https://github.com/meganz/megacmd)

---

### Post by mikelodeon13 on 2018-03-20
Hello,

I was able to do what I wanted but I used megatools instead. Right now I'm working on it and it is what I was expecting. Everybody thanks for your time and for sharing your knowledge.

Have a great day.....

---

