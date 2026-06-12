---
title: "trying to execute a node.js script through ubuntu"
date: 2014-12-29
forum: General Help
---

### Post by random512 on 2014-12-29
Hello, I'm trying to execute a node.js script through ubuntu. I'm using the basic webserver example on the node.js homepage ([http://nodejs.org/](http://nodejs.org/)).  I've uploaded the js file to my ubuntu server and I used tree to validate that the js file exists in the expected directory on the server. The file is named Example.js. I tried the following command:


sudo node Example.js


I also tried:


node Example.js


The result of both attempts was that the console simply prompted a new line. I also tried the command for a file that did not exist:


node Example2.js


This action had the same result as the 2 previous attempts. The console simply prompted a new line. I would expect an error output like "file does not exist" or something similar to that. Should I have expected the first 2 commands to work?  If so then what should have been the output? Why did the expected error test not output an error?  I think I'm missing 1 or more pieces in my understanding of how to execute and validate programs on ubuntu.

---

### Post by Holger_Gehrke on 2014-12-29
If it had worked, you would have seen this
```
Server running at http://127.0.0.1:1337/
``` 
in the shell and it would **not** give you a new prompt because the script was still running. If you then ran a browser and went to that url, the response in the browser would have been 'Hello World'

Did you install node from the tarball on the page or through apt ?
I took the tarball (didn't have it installed before, and they warn about packages of node.js always being old and stale) unpacked it in ~/bin; cd ~/bin/node-v0.10.35-linux-x86/bin; copied and pasted the example into gedit and saved it in that directory. Than I ran ./node ex.js and it worked.

Edit:
And this is what  a wrong file name for a script should look like
```

./node blub.js

module.js:340
    throw err;
          ^
Error: Cannot find module '/home/user/bin/node-v0.10.35-linux-x86/bin/blub.js'
    at Function.Module._resolveFilename (module.js:338:15)
    at Function.Module._load (module.js:280:25)
    at Function.Module.runMain (module.js:497:10)
    at startup (node.js:119:16)
    at node.js:929:3

```

---

### Post by random512 on 2014-12-29
thanks holger.  good info.  I found the following info online regarding a recommended installation strategy of node.js on ubuntu:

sudo apt-get install python-software-propertiessudo add-apt-repository ppa:chris-lea/node.js
sudo apt-get update
sudo apt-get install nodejs

Are you recommending that I:

1. copy the latest tarball from [http://nodejs.org/download/](http://nodejs.org/download/) 
2. paste it into the ubuntu bin dir through WinSCP
3. unpack the tarball on the server using defaults

Sorry if I'm missing something.  I'm brand new to ubuntu/linux.

---

### Post by random512 on 2014-12-29
I downloaded the tarball and tried to copy it over to the bin dir on the remote server through WinSCP.  However, WinSCP displayed an error dialog:

Cannot create remote file '/bin/test.txt.'
Permission denied.
Error code: 3
Error message from server: Permission denied

Any idea how I can fix this permissions issue?

---

### Post by Holger_Gehrke on 2014-12-29
yes to 1. no to 2. and 3. 
/usr/local is the directory hierarchy for locally installed, non-package-managed software that should be available to all users of the machine.
If there are other users on the server who don't want or need node.js, you should think about setting it up in a private directory. There's some links on nodejs.org to articles and posts on just this topic.

---

### Post by Holger_Gehrke on 2014-12-29
You have to be root to write in /bin or /usr/bin or /usr/local/bin. If you can't do that, then you should do what I mentioned in my last post and set up a private directory for nodejs in your home directory.

---

### Post by random512 on 2014-12-29
I'm not able to copy the tarball to /bin or /usr/bin or /usr/local/bin. I'm not sure what you mean by "you have to be root" to write in those dirs. I'm the owner of my own aws ec2 instance so I think I should have the ability to grant any permissions I want. I'm currently logged in as "ubuntu" to my ubuntu server because I think that's the default. Does this sound like an AWS permissions config problem that I should post to an AWS forum?

---

### Post by QIII on 2014-12-29
Hello!

Ubuntu probably doesn't know, or care, that it is running on Amazon's EC2.  The advice given means that you need to have root (or elevated) system privileges.  

Are you prefacing your commands as you try to move the file(s) with "sudo" to do so?

---

### Post by random512 on 2014-12-30
hi q - thanks for the response. I'm currently trying to copy a file from my local directory to the ubuntu server through WinSCP. Since it's a gui tool I'm not using commands so there's no way to preface with sudo.  Are you aware of any type of system setting that can be set in WinSCP to set sudo rights?

---

### Post by Holger_Gehrke on 2014-12-30
Why don't you scp the tarball into your home directory and then ssh into the server, unpack the archive and copy the files on the command line ?
If you can use scp, you should have an ssh account unless the configuration on the server is very restrictive. If you don't have an ssh-client on windows, I would recommend PuTTY.

Also if all the talk about 'having root' and 'permissions' confuses you, you really should read up on Unix and Linux basics. Short version: every file has an owner and a group. There's three sets of three permission - read, write and execute for the owner, the group and all others - for every file and a directory is just a file with a certain structure and a set 'directory'-attribute. '/usr' on Ubuntu is owned by 'root' - the administrator - and belongs to the group 'root'. Only the owner has permission to write there.

'sudo' means '**s**witch **u**ser and **do**' and is a tool to temporarily elevate your permissions.

There are some assumptions about the various 'bin' directories you should know:
- '/bin' is for programs that have to be available at any time after the Kernel has mounted '/', even before the network is up ('/usr/ might be imported from a net and not available yet)
- '/usr' (Unix System Resources) on Linux is assumed to contain stuff that's maintained by the package manager, with the exception of
- '/usr/local' which is meant for locally developed / compiled software that should be available to all users of  the system,

If you want some programs just to try them out yourself, create a 'bin' directory in your $HOME and add it to your $PATH.

---

