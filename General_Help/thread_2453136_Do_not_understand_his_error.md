---
title: "Do not understand his error"
date: 2020-11-03
forum: General Help
---

### Post by jack0987 on 2020-11-03
Does anyone know how to fix this?

w12admin@W12:~$ cd eth
w12admin@W12:~/eth$ export PATH=$PATH:/usr/local/go/bin
w12admin@W12:~/eth$ go get github.com/ethereum/go-ethereum
# github.com/ethereum/go-ethereum/crypto/secp256k1
exec: "gcc": executable file not found in $PATH
w12admin@W12:~/eth$

---

### Post by TheFu on 2020-11-03
```
exec: "gcc": executable file not found in $PATH
```

Did you install gcc and all the other dependencies to build C/C++ software?

---

### Post by jack0987 on 2020-11-04
> **TheFu said:**
> ```
exec: "gcc": executable file not found in $PATH
```

Did you install gcc and all the other dependencies to build C/C++ software?

I did this:

wget [https://dl.google.com/go/go1.15.2.linux-amd64.tar.gz](https://dl.google.com/go/go1.15.2.linux-amd64.tar.gz)
tar -xvf go1.15.2.linux-amd64.tar.gz
sudo mv go /usr/local

---

### Post by norobro on 2020-11-04
As @Fu asked, do you have gcc installed?

Form the docs: [https://github.com/ethereum/go-ethereum/wiki/Installation-Instructions-for-Ubuntu#user-content-building-from-source](https://github.com/ethereum/go-ethereum/wiki/Installation-Instructions-for-Ubuntu#user-content-building-from-source)
> [COLOR=#24292E][FONT=-apple-system]Building [/FONT][/COLOR]geth[COLOR=#24292E][FONT=-apple-system] requires Go and C compilers to be installed:
[/FONT][/COLOR][COLOR=#24292E][FONT=SFMono-Regular]
  sudo apt-get install -y build-essential[/FONT][/COLOR]

---

### Post by TheFu on 2020-11-04
> **jack0987 said:**
> I did this:

wget [https://dl.google.com/go/go1.15.2.linux-amd64.tar.gz](https://dl.google.com/go/go1.15.2.linux-amd64.tar.gz)
tar -xvf go1.15.2.linux-amd64.tar.gz
sudo mv go /usr/local

That appears to be "no, I didn't install gcc and the other C/C++ dependencies."  There are hundreds of guides for this, so I won't repeat here. There are packages for these things, so look for some **apt-get install** or **apt install** commands with package names like  ... gcc.  I haven't needed to do that in a few years, since I'm not a C code monkey anymore.

Is there a specific reason to get go from some dl.google.com site?  That seems pretty dangerous, unless a very trusted person who you personally know and trust, suggested it.  I've never pulled code from there or dropbox.  Just not something I'd do. If you need a specific golang branch, I bet they have an official git repo you can clone.

But it is your box. Do what you feel is correct. I'm just some random guy on the internet too.

---

### Post by SeijiSensei on 2020-11-05
```
sudo apt install build-essential
```

should solve any gcc problems.

---

### Post by HermanAB on 2020-11-05
I would uninstall go, then install the build essentials and after that do this:
[https://wiki.ubuntu.com/Go](https://wiki.ubuntu.com/Go)

---

