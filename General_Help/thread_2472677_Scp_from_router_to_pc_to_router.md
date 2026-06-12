---
title: "Scp from router to pc to router"
date: 2022-03-08
forum: General Help
---

### Post by jimninja on 2022-03-08
Hi,
  I would like to copy File with SCP in script.
I explain here, from router ssh session, the script is running from   router, i need to SCP to my PC, and take the file to my router.
  But what I try does not work, cause I can't exit from my script or I cant stop router ssh session to SCP PC to router.
I need to stay in my router session and take file and bring it back, is it possible?

---

### Post by TheFu on 2022-03-08
scp can pull or push files.
Which "script" language do you intend to use?

Whatever you would normally type, put that into a file. Setup the #! line for the scripting language you like, chmod +x on this file and run it.

scp is for copying files only. It doesn't open an interactive session.  If you want to make a single connection then pull and push files in that same connection, use sftp. The get and put commands from normal, plain, FTP work exactly the same.

scp is a replacement for rcp. The semantics are identical.
sftp is a replacement for plain FTP.  The semantics are identical. There is a way to pass in an FTP script to sftp to make connections, chdir local and/or remote, and to put/pull files or mput/mpull files, just like plain FTP, except with the security of ssh.

So, if you will create some pseudo-code (call them "code comments") and post those here, we can provide leads so you'll learn to do this yourself next time.  There are many, many, how-to guides for this. Have you tried any of those already?  [https://www.computerhope.com/unix/sftp.htm](https://www.computerhope.com/unix/sftp.htm) has all the options (so does your local sftp manpage on the machine).  Not the -b option?

---

### Post by MAFoElffen on 2022-03-09
SCP is not a common utiltiy on routers, even if they support SSH. I have used scripts to interact with console, to redirect output of the stdout to files while in an SSH session with a router, but...

Usually for routers, to add files to routers, or to download from (move files between) you enable and configure ftp to it then upload and download through ftp. 

What Kind of router are you talking about? Because that affects the CLI it uses and the capabilities it has... Unless you are talking about a hacked router, such as with DD-WRT, RouterOS, ZeroShell or Untangle, where the router is reflashed and is running Linux as it's OS... Instead of Cisco iOS, Dell Networking OS X, HP Networking CLI, etc...

My scripts for the later... Are all in the specific CLI languages of those routers and switches. 

So yes... Your question needs some context and information on what you are trying to do with what...

Let's say the router does understand SCP... In a bash script... "If" I am in an SSH session with another Linux device, and I want to transfer a file between, then I issue the SCP command on the remote device, as if I was there... in SSH session local to remote, to send a file from the remote to me, I do:
```

scp /path/on/remote/file my_username@my_location:/path/to/file

```
Like I said... Just like I am there. Sending the file from it as the source, back to me as the target. You do not have to disconnect or open another session (in your script, at your location) to do that. Like I used to tell my CS students: *"Always remember your source and target. It's all a matter of perspective..."*

 Why do you say you would have to disconnect to do that? I don't understand that... In reality, in a script with a connected SSH session, you are local in a tty session and connected as a pts session on that device... as if you were local there, right? You can issue that command back to you as if you were 'that remote session'. It will open that next connection back to you. It's simple when you think of it that way, right. Remember where you are, when you ask for things.

*"It's all a matter of perspective..."*

---

### Post by ActionParsnip on 2022-03-09
If you setup SSH keys then you won't be asked for authentication too. SCP can push and pull file so you don't need to be on the router to access data

---

### Post by TheFu on 2022-03-09
> **MAFoElffen said:**
>  
 Why do you say you would have to disconnect to do that? I don't understand that... In reality, in a script with a connected SSH session, you are local in a tty session and connected as a pts session on that device... as if you were local there, right? You can issue that command back to you as if you were 'that remote session'. It will open that next connection back to you. It's simple when you think of it that way, right. Remember where you are, when you ask for things. 

I suspect the 'session' is because 2 commands would be needed if scp is used and each would make new connection with new authentication. That's why I suggested using sftp - though really, using scp would be much simpler even if 2 connections are needed. sftp would need to use an external sftp/ftp script file, adding to the complexity ... or a 'heredoc' which someone asking the questions is unlikely to understand (though if they are told exactly what to type, it will work too).

Good point on asking about the routerOS and the limitations.  I've been using BSD and Linux based router OSes for so long as to forget that the big commercial vendors don't usually handle what we consider common protocols.  Just getting Cisco (and other popular, but now dead vendors) to support ssh was like pulling teeth - they wanted tftp and telnet to be used forever. After all, the management interface should be on a separate subnet, inaccessible to unauthorized clients.  Their suggestion to make that part of the design doesn't make it happen.  We can still find cisco WAN routers on the internet with telnet ports open to the world today.  A quick Shodan search will find them.  It is amazing what that tool finds ... out in the world, with default passwords.

---

