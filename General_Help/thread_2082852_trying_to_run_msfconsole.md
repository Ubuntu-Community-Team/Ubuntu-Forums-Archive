---
title: "trying to run msfconsole"
date: 2012-11-10
forum: General Help
---

### Post by wingnut2626 on 2012-11-10
when I attempt to run msfconsole from the command line this is what I get:

```
Welcome to fizsh, the friendly interactive zshell
Type man fizsh for instructions on how to use fizsh
john@whatitis ~> msfconsole

Call trans opt: received. 2-19-98 13:24:18 REC:Loc

     Trace program: running

           wake up, Neo...
        the matrix has you
      follow the white rabbit.

          knock, knock, Neo.

                        (`.         ,-,
                        ` `.    ,;' /
                         `.  ,'/ .'
                          `. X /.'
                .-;--''--.._` ` (
              .'            /   `
             ,           ` '   Q '
             ,         ,   `._    \
          ,.|         '     `-.;_'
          :  . `  ;    `  ` --,.._;
           ' `    ,   )   .'
              `._ ,  '   /_
                 ; ,''-,;' ``-
                  ``-..__``--`


       =[ metasploit v4.5.0-dev [core:4.5 api:1.0]
+ -- --=[ 981 exploits - 530 auxiliary - 162 post
+ -- --=[ 262 payloads - 28 encoders - 8 nops
       =[ svn r16053 updated yesterday (2012.11.08)

[*] Processing /home/john/.msf4/msfconsole.rc for ERB directives.
resource (/home/john/.msf4/msfconsole.rc)> exit
john@whatitis ~>

```

why does it automatically exit?

---

### Post by crushkittykitty on 2012-11-10
Were did you install it? looks like its pointing to the wrong folder mine is installed in the /opt/msf4 are you running as sudo? what happens when you type msfupdate 












									[http://ubuntutheotheros.webs.com/](http://ubuntutheotheros.webs.com/)

---

### Post by crushkittykitty on 2012-11-10
try    sudo msfconsole 
instead of  msfconsole 









more hints and tricks here.
[http://ubuntutheotheros.webs.com/](http://ubuntutheotheros.webs.com/)

---

