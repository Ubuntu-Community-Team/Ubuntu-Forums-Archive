---
title: "Cannot Install Opensnitch"
date: 2018-11-26
forum: General Help
---

### Post by shane_faulkinbury2 on 2018-11-26
I'm trying to install Opensnitch following this url, 
[https://itsfoss.com/opensnitch-firewall-linux]("https://itsfoss.com/opensnitch-firewall-linux") 
and I'm stuck at the ```
go get github.com/golang/protobuf/protoc-gen-go

```  command.

This is what I get ```
cd /snap/binroot@sup-HP-Compaq-8200-Elite-SFF-PC:/snap/bin# go get github.com/golang/protobuf/protoc-gen-go
Command 'go' is available in '/snap/bin/go'
The command could not be located because '/snap/bin' is not included in the PATH environment variable.
go: command not found

```

What do I need to do to finish the install?

---

### Post by again? on 2018-11-27
Tutorial says ...
> Before you start, you need to have Go properly installed and the $GOPATH environment variable is defined.
```
sudo apt install golang
echo "export GOPATH=$HOME/go" >> ~/.bashrc
source ~/.bashrc

```

Check $GOPATH...
```
echo $GOPATH
```

---

### Post by shane_faulkinbury2 on 2018-11-27
I installed it, but didn't look at where it installed to.  Thanks

---

### Post by shane_faulkinbury2 on 2018-11-27
I get down to switch to the $GOPATH directory and I get this.  ```
cd $GOPATH/src/github.com/evilsocket/opensnitch
bash: cd: /src/github.com/evilsocket/opensnitch: No such file or directory
```

I don't even have a src directory!

---

### Post by shane_faulkinbury2 on 2018-11-27
Never mind, I found it.  Now I get this after i run the sudo make install command.

```
/home/sup/go/src/github.com/evilsocket/opensnitch# sudo make install
make[1]: Entering directory '/home/sup/go/src/github.com/evilsocket/opensnitch/daemon'
cp: cannot stat 'opensnitchd': No such file or directory
Makefile:4: recipe for target 'install' failed
make[1]: *** [install] Error 1
make[1]: Leaving directory '/home/sup/go/src/github.com/evilsocket/opensnitch/daemon'
Makefile:4: recipe for target 'install' failed
make: *** [install] Error 2

```

---

### Post by shane_faulkinbury2 on 2018-11-27
I tried to use Makefile instaed of Make since it's in the directory and this is what I got.

```
/home/sup/go/src/github.com/evilsocket/opensnitch# sudo Makefile install
sudo: Makefile: command not found
```

---

### Post by again? on 2018-11-27
Where you're at now is beyond my level of understanding.
Hopefully someone else can help you.

---

### Post by again? on 2018-11-28
Try this recent tutorial (requires ubuntu 17.10 or newer) which says to use **sudo [COLOR="#FF0000"]-H[/COLOR] make install** to target the user's home directory.
[How To Install OpenSnitch Application-Level Firewall In Ubuntu]("https://www.linuxuprising.com/2018/04/how-to-install-opensnitch-application.html")

---

### Post by shane_faulkinbury2 on 2018-11-28
If anyone could help me out from the link provided above.  I'm on the final step, but I can't figure out what is wrong. I run a ```
sudo make install
```  and get this.    ```
~/go/src/github.com/evilsocket/opensnitch$ sudo make install
make[1]: Entering directory '/home/sup/.local/share/Trash/files/src/github.com/evilsocket/opensnitch/daemon'
cp: cannot stat 'opensnitchd': No such file or directory
Makefile:4: recipe for target 'install' failed
make[1]: *** [install] Error 1
make[1]: Leaving directory '/home/sup/.local/share/Trash/files/src/github.com/evilsocket/opensnitch/daemon'
Makefile:4: recipe for target 'install' failed

```

Here is what is in the directory.

---

### Post by logix2 on 2018-11-29
It looks like you deleted some folders in the process (the daemon folder is in your Trash). It's probably best to delete the ~/go folder (if it's only for Opensnitch and nothing else) and start from the beginning.

---

### Post by shane_faulkinbury2 on 2018-11-29
I'll do that, but even better, how do I get rid o go completely and start from scratch?

---

### Post by shane_faulkinbury2 on 2018-12-02
I get stuck when running the make command because there is no make just a makefile!

---

