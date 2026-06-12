---
title: "Update error (Key expired)"
date: 2017-06-29
forum: General Help
---

### Post by avasquezve on 2017-06-29
Hi everyone!!

I am trying to update my ubuntu v.16.04 and the system throws the following error
[INDENT]
[/INDENT]
[INDENT]
[/INDENT]
[INDENT]W: An error occurred during signature verification. The repository is not updated and the use of the old index files. GPG Error: 

[http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04](http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04) Publication: The following signatures are invalid: KEYEXPIRED 1496576244

[/INDENT]
[INDENT]W: Failed to get [http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04/Release.gpg](http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04/Release.gpg) The following signatures are invalid: KEYEXPIRED 1496576244

[/INDENT]
[INDENT]W: Some index files could not be downloaded, omitted or used in the past.[/INDENT]


I wish I could receive support from you, thank you very much!

---

### Post by slickymaster on 2017-06-29
Hello avasquezve, welcome to the forums.

Please open a terminal window (Ctrl+Alt+T) and run the following commands, one at a time```
sudo apt-get clean
sudo mv /var/lib/apt/lists /tmp
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update
```

---

