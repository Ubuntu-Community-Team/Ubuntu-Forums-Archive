---
title: "update-alternatives install error: error creating symbolic link 'go.dpkg-tmp'"
date: 2015-08-10
forum: General Help
---

### Post by Kurtosis on 2015-08-10
Hi all, I'm trying to install Go 1.4.2 using the Alternatives system, but getting an error I don't understand yet:

```
update-alternatives: using /opt/go/1.4.2/bin/go to provide /usr/local/go/bin/go (go) in auto mode.
update-alternatives: error: error creating symbolic link `/usr/local/go/bin/go.dpkg-tmp': No such file or directory
```

I can't find anything on this 'dpkg-tmp' file that Update Alternatives uses, I assume temporarily since it doesn't exist for any other packages I've installed this way, just Go.  I've attached my install script, as well as strace output from running that script.  There's very little info on this on the internet or in Debian/Ubuntu docs about how alternatives works exactly.  Any ideas or pointers for how to troubleshoot it would be much appreciated.

---

### Post by Kurtosis on 2015-08-11
Solved - problem is the target directory /usr/local/go/ doesn't exist.  Have to manually create it and all subdirectories referenced in the install.sh script.

The problem then becomes that go's canonical installation location /usr/local/go is not in the system path, nor is the same as the Ubuntu repo version of go (golang-go), /usr/bin and /usr/lib.  So question - should the alternatives install script configure and install Go the former or latter way?  Not sure, will experiment with both and update.

Update - after some experimentation I gave up on using update-alternatives to manage multiple go versions, just too complicated.  Easier way is to unpack all desired Go versions to /opt/go/$VER, then softlink /opt/go/default to whichever you want to be the current version, then softlink /opt/go/default to Go's default $GOPATH location /usr/local/go.  When you want to change versions, change /opt/go/default to point at a different /opt/go/$VER.

This seems necessary b/c update-alternatives doesn't seem to play well with directories, only files, and specifically binary files.  To use the Alternatives system it seems you would have to script every file in every folder in the Go package, otherwise Go won't be able to find them.

---

