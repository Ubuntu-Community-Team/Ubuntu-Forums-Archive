---
title: "Installing megacmd in Ubuntu (console only)"
date: 2019-08-11
forum: General Help
---

### Post by mangonels on 2019-08-11
Hello. My final objective is to make a timed backup system capable of sending a folder in Ubuntu to mega.nz

For that purpose, I thought it would be a good idea to install a program I heard of, called megacmd.

I followed various tutorials, including the one on megacmd's github, however I always get stuck in some part of them.

The last tutorial I followed which seemed rather easy for an inexperienced ubuntu user like me is this one:[URL="https://www.seedhost.eu/whmcs/knowledgebase/227/megacmd-installation.html"]
https://www.seedhost.eu/whmcs/knowledgebase/227/megacmd-installation.html[/URL]

However I am stuck in step 7, after having input all of the commands exactly, (using root user). This error appears:

```

root@ns360684:~/megacmd# GOROOT="${HOME}/go" makego build -o megacmd
main.go:14:2: cannot find package "github.com/t3rm1n4l/go-mega" in any of:
        /root/go/src/pkg/github.com/t3rm1n4l/go-mega (from $GOROOT)
        ($GOPATH not set)
main.go:15:2: cannot find package "github.com/t3rm1n4l/megacmd/client" in any of:
        /root/go/src/pkg/github.com/t3rm1n4l/megacmd/client (from $GOROOT)
        ($GOPATH not set)
Makefile:8: recipe for target 'build' failed
make: *** [build] Error 1
root@ns360684:~/megacmd# main.go:14:2: cannot find package "github.com/t3rm1n4l/go-mega" in any of:
main.go:14:2:: command not found
root@ns360684:~/megacmd#         /root/go/src/pkg/github.com/t3rm1n4l/go-mega (from $GOROOT)
-bash: syntax error near unexpected token `from'
root@ns360684:~/megacmd#         ($GOPATH not set)

```

If anyone has a better backup system idea let me know. I chose mega because it offers the most space.

---

### Post by Holger_Gehrke on 2019-08-11
You are aware that mega.co.nz offers precompiled binaries in various package-formats including .deb for all supported Ubuntu versions and also has a repositories for use with apt at [https://mega.nz/linux/MEGAsync/](https://mega.nz/linux/MEGAsync/) ? 
No need to install from source unless you want to ...

Holger

---

### Post by dragonfly41 on 2019-08-11
Just to address this clue $GOPATH not set

run command ```
go env
``` and you will see that $GOPATH needs to be specified.

[https://stackoverflow.com/questions/21001387/how-do-i-set-the-gopath-environment-variable-on-ubuntu-what-file-must-i-edit/27491937#27491937](https://stackoverflow.com/questions/21001387/how-do-i-set-the-gopath-environment-variable-on-ubuntu-what-file-must-i-edit/27491937#27491937)

---

### Post by mangonels on 2019-08-11
Holger, I found a few files for ubuntu but I'm clueless as to what I should do with them.

---

### Post by Holger_Gehrke on 2019-08-12
Set up the repository by adding a file for it by running 'sudoedit /etc/apt/sources.list.d/mega-nz.list'. Put a line like this (but with the version of Ubuntu you're running instead of '18.04') in the file 
```

deb https://mega.nz/linux/MEGAsync/xUbuntu_18.04/ ./

```
Save and exit the editor. Next get the signing key for the repository
```

curl -fsSL https://mega.nz/keys/MEGA_signing.key | sudo apt-key add -

```
Run 'sudo apt update' to update the list of available packages. To install megacmd run 'sudo apt install megacmd'. The advantage of doing it this way is that updates of megacmd will be automatically fetched and installed when you upgrade your packages.

Alternatively you could just download the .deb-file that is right for your machine and the version of Ubuntu you're running from mega.nz and double-click the downloaded file to install it (.deb files are normally associated with gnome-software, which will install them).

Holger

---

### Post by mangonels on 2019-08-12
Thank you. This was so helpfull!

---

