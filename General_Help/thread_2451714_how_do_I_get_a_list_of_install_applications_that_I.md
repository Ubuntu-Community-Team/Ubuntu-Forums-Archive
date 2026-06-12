---
title: "how do I get a list of install applications that I installed myself?"
date: 2020-10-09
forum: General Help
---

### Post by ardouronerous on 2020-10-09
I'd like to know if there's a terminal command to find out what applications that was installed by the user, excluding those that are installed by default by the operating system and installed by the operating system via updates, and pipe the results into a txt file.

I'm going to upgrade from 18.04 to 20.04 next month and I'd like to get the list so reinstallation is a breeze. Thanks.

I've looked into [FONT=courier new]/var/log/apt/[/FONT] and the history logs are confusing.

---

### Post by dragonfly41 on 2020-10-09
Two sources I look at ..

(a) run command .. history | grep install

and

(b) Synaptic Package Manager .. File > History

---

### Post by rbmorse on 2020-10-09
Create the list of manually installed packages and save it in a file named "apt-mark.manual":


```
sudo apt-mark showmanual >apt-mark.manual
```

---

### Post by &amp;KyT$0P# on 2020-10-10
> **ardouronerous said:**
> I'd like to know if there's a terminal command to find out what applications that was installed by the user, excluding those that are installed by default by the operating system and installed by the operating system via updates, 

No there is not.  [But you can write a script.]("https://ubuntuforums.org/showthread.php?t=2355157&p=13618967&viewfull=1#post13618967")

---

### Post by ActionParsnip on 2020-10-10
```
 
history | egrep 'apt|dpkg'

```

Will do it. You can cycle through all users with a BASH loop easily 
```

for i in `cat /etc/passwd" | cut -d":" -f 1`
do
echo $i
sudo -u $I history | egrep 'apt|dpkg'
done

```

---

### Post by Impavidus on 2020-10-11
history will only show what was installed by command line and only goes back a thousand commands or so.

---

### Post by oldfred on 2020-10-11
It does not download & reinstall any apps already installed, so the complete list is ok to use.

My backup includes this also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)


I now run a script that installs 90% of what I want.
Then I will run the dpkg output from old install after reviewing long list to make sure I do not have somethings that are not really required or will install if ever needed again.

---

