---
title: "Change javac version and target"
date: 2015-07-16
forum: General Help
---

### Post by Alexander_Mogren on 2015-07-16
Hi.

I have a problem. I want to change the version and target from javac 1.8 to 1.7.

I figured that I could run command:
```
javac -source 1.7 -target 1.7
```

When I do I get the following:
```
javac: no soruce files
```

So I just used the command with the "-target 1.7" and I got this instead:
```
javac: target release 1.7 conflicts with default source release 1.8
```

Thanks.

---

### Post by Alexander_Mogren on 2015-07-16
Hi.

I have a problem. I want to change the version and target from javac 1.8 to 1.7.

I figured that I could run command:
```
javac -source 1.7 -target 1.7
```

When I do I get the following:
```
javac: no soruce files
```

So I just used the command with the "-target 1.7" and I got this instead:
```
javac: target release 1.7 conflicts with default source release 1.8
```

Thanks.

---

### Post by monkeybrain20122 on 2015-07-16
You need to update-alternatives. Easy way with a gui install galternatives then you can pick your default with a click.

---

### Post by monkeybrain20122 on 2015-07-16
Duplicated thread. I replied on the other one.

---

### Post by Alexander_Mogren on 2015-07-16
Installed "Alternatives Configurator" it did not work. When trying to change the default it just jumps back to 1.8.
It worked better almost as always to do it in termnial. Thanks for big help

---

### Post by monkeybrain20122 on 2015-07-16
> **Alexander_Mogren said:**
> Installed "Alternatives Configurator" it did not work. When trying to change the default it just jumps back to 1.8.
It worked better almost as always to do it in termnial. Thanks for big help

Well there was a bug in galternatives in 14.04 but I thought it was fixed. Anyway to do it in the terninal
[http://askubuntu.com/questions/121654/how-to-set-default-java-version](http://askubuntu.com/questions/121654/how-to-set-default-java-version)

---

### Post by PaulW2U on 2015-07-16
Threads merged.

Please don't start duplicate threads as it causes confusion, thanks.

---

