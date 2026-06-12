---
title: "php to linux shell"
date: 2013-02-21
forum: General Help
---

### Post by fafabone on 2013-02-21
Hi All,
I'm using Kubuntu 12.04, but the asking is general.
I would like to launch linux commands via php. That because I would like to send remotely commands, inside my home network that has WS, Android and Kubuntu.
I installed lampp from the ubuntu repository
I started with commands that konsole executes perfectly, as well as firefox, that launches the browser. In php:
$output = shell_exec('firefox 2>&1')
The output returned is: 
/usr/lib/firefox/firefox:  /opt/lampp/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required  by /usr/lib/i386-linux-gnu/libstdc++.so.6)
Can you help me, or can you just suggest a guide to understand better the problem?
Thanks
Have a nice day

---

### Post by prodigy_ on 2013-02-21
Why PHP and not SSH? ```
ssh username@remote_host command
```

---

### Post by TheFu on 2013-02-21
> **prodigy_ said:**
> Why PHP and not SSH? ```
ssh username@remote_host command
```

Php has a low entrance barrier.  Allowing PHP to run remote commands from a web site is .... er ... **extremely dangerous.**  This is how websites get hacked.  That means that php configurations usually try to prevent this.  That probably happened when you installed the lamp stack.  Most system scripts that I see are not written in php for this reason.  They are written in bash, sh, perl, python, ruby .... almost anything except php.

However, if doing this without a web server involved, it is a pure PHP question, which I honestly cannot answer, but to run system commands in almost every language I know, you use something like 
```
system("/path/to/the/command -options-for -the-command");
```
or 
```
`/path/to/the/command -options-for -the-command`;
```

If those commands need to be remote, ssh is definitely the best tool for the job, unless you need/want to do it over HTTP/json or xml or REST. But as a php programmer, you should already know how to make that stuff work.

---

### Post by Habitual on 2013-02-21
example:
[http://www.bournetoraiseshell.com/article.php/20121004115956953](http://www.bournetoraiseshell.com/article.php/20121004115956953)

---

### Post by fafabone on 2013-02-24
> **Habitual said:**
> example:
[http://www.bournetoraiseshell.com/article.php/20121004115956953](http://www.bournetoraiseshell.com/article.php/20121004115956953)

Uhm..nice suggestion! Instead of ssh command could I send a shell command directly?
Could you briefly explain the syntax of
$output = shell_exec("ssh -qi /home/jj/.ssh/somekey_rsa user@123.456.789.123 w | awk -F "$FTEXT" '{ print $2 }'");
ssh is a shell command or it should be in the folder of the script? /home/jj/.ssh/somekey_rsa is the script to be executed? w | awk is a single command? 
Now that I know what I need to investigate, I feel the result very near. :P
Thank you!

---

### Post by TheFu on 2013-02-24
> **fafabone said:**
> Uhm..nice suggestion! Instead of ssh command could I send a shell command directly?
Could you briefly explain the syntax of
$output = shell_exec("ssh -qi /home/jj/.ssh/somekey_rsa user@123.456.789.123 w | awk -F "$FTEXT" '{ print $2 }'");
ssh is a shell command or it should be in the folder of the script? /home/jj/.ssh/somekey_rsa is the script to be executed? w | awk is a single command? 
Now that I know what I need to investigate, I feel the result very near. :P
Thank you!

If 2 different machines are involved, there needs to be a client and a server.  Most Linux systems run ssh as a client. It is the preferred method to have secure communications. Most other network tools that are client and server, do not provide security - netcat or telnet are examples. These should be avoided due to the security issues, however, some people will use them still because of the perceived ease of use and belief that security is not necessary on an internal LAN.

ssh is one of those tools that both improves security AND makes connecting systems more convenient through the use of PKI (keys for everyone else).

If you want to send a remote command to another machine, you need a client on the current machine and a server on the remote machine.  The server "listening" on the remote machine will dictate which "client" can be used.  There are lots of different servers - heck, you could create a REST-ful interface on the remote server using PHP and a web server that runs commands locally. This may be a great idea or it may be a terrible idea, depending on the use case.

ssh is really the best option that I know for general - "run this command on that remote server" needs, but there are at least 300 other options too. Most will not be as secure as SSH, since ssh encryption is secure enough for tunnels across the internet.  ssh replaced the non-secure tool, rsh. Most Linux systems do not install rsh anymore - it is generally considered a terrible idea to use rsh or any of the "r-commands" anymore due to security considerations.

Some other C/S examples that you could implement include: HTTP/REST, Java-JNI, CORBA, RPC/sockets, netcat, rsh.

Is there a reason that you don't want to use ssh?  Are you trying to create a back-door?

---

### Post by fafabone on 2013-02-24
No, the reason is that I'm new in the Linux world and I don't know well the potentiality of this kind of OS. I know well php, javascript and HTML, so an idea I had involves Chrome for the vocal command, then ajax requests to send the command to the server and php to take the commands and translate them in linux shell commands. 
The ssh connection between the system and lampp server is what I need. 
It is the only passage where I fail:D
I'm studying ssh :lolflag:

---

### Post by TheFu on 2013-02-24
> **fafabone said:**
> No, the reason is that I'm new in the Linux world and I don't know well the potentiality of this kind of OS. I know well php, javascript and HTML, so an idea I had involves Chrome for the vocal command, then ajax requests to send the command to the server and php to take the commands and translate them in linux shell commands. 
The ssh connection between the system and lampp server is what I need. 
It is the only passage where I fail:D
I'm studying ssh :lolflag:
If all that you need is for a web browser to request a php webpage to do something on the server where the webpage runs, then you do not need ssh. Local commands are just made using whatever system() routine that php supports.  Just know that the environment will be restricted for security reasons and limited to whatever permissions the account running the php code (web server?) has.

You would only want to use ssh if there were a 3rd computer involved AND you must have the webserver involved.

**If you only need to run remote commands on any UNIX/Linux computer and do not need a web server involved for some other, specific, reason, using ssh with key-based authentication IS the best solution. **This is for non-GUI programs - also called terminal or CLI or shell programs.

After re-reading your OP, it could be that we completely missed what you were trying to do.  If you want to run remote programs that use a GUI, then things become more complicated. This article tries to explain the different methods available and how to use each: [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)

In short, there is little need to use php for this stuff, unless you must for some other reason.

---

### Post by malish on 2013-02-24
If you just want to execute commands on one of the machines, no matter with or without a web browser, just use the SSH.  That's readily and perfectly available.  You just have to install an ssh server on the machine that should execute the commands and connect using ssh command from the other machine.

However, if you still wanna fix the PHP code, that error is not because your code is wrong. It is because you should have libgcc1 that is used by PHP modules.  Probably, installing it by running the following command on the machine on which you have installed PHP would fix it:

```
sudo apt-get install libgcc1
```-------
[http://m.a.sharpasand.com/](http://m.a.sharpasand.com/)

---

### Post by fafabone on 2013-03-24
Ok, now, I've installed openssh on Ubuntu, and I have installed:
"apt-get install libssh2-1-dev libssh2-php"
Now ssh2 function properly with php installed via ubuntu repository, but I've installed lampp and I would let ssh work under this server. 
Can you explain wich files I need to copy and where? How do I need to modify php.ini? I read about extension = ssh2.so
Then, how can I identify the authetication type of my system? It seems a plain password, but I remember that I created id_dsa file with keygen command. So what do I need to do to connect openssh via php ssh2 extension?
Thanks

---

### Post by SeijiSensei on 2013-03-24
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by fafabone on 2013-03-24
Thanks. What about ssh2 extension installation in lampp server?

---

### Post by fafabone on 2013-03-25
Can anybody help me?

---

