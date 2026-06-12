---
title: "error installing automix"
date: 2006-11-21
forum: General Help
---

### Post by gustav213 on 2006-11-21
hey well i wanted to install firefox 2 and read that by installing automix i could get it to work so i went to here website and put the script in the terminal and then it told me to update it and i did and i got this error.


W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C


dont know what it is any help.

---

### Post by taurus on 2006-11-21
Did you also install the key for it???

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29)

---

### Post by gustav213 on 2006-11-21
hey thanx i think it works, just need to get home and use the live cd, since it asks for it, can anyone explain why it does that its not the first time it has asked for it, just curious. thanx again.

---

### Post by taurus on 2006-11-21
Because it needs to install more stuff from the CD.  If you don't want it to use the CD, command out the first line in /etc/apt/sources.list...

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by gustav213 on 2006-11-21
hey so if i get this right it should look like this right. 

 echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main" | gksudo gedit /etc/apt/sources.list
 wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
 gpg --import key.gpg.asc
 gpg --export --armor 521A9C7C | sudo apt-key add -

and then i do the apt get update and apt get install automatix2. it says it cant be validated bt i just keep on going right. 

thanx a lot,

---

### Post by taurus on 2006-11-21
> **gustav213 said:**
> hey so if i get this right it should look like this right. 

 echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main" | gksudo gedit /etc/apt/sources.list
:confused:  :confused:  :confused: 

```
echo "deb http://www.getautomatix.com/apt dapper main" | sudo tee -a /etc/apt/sources.list
```

---

### Post by gustav213 on 2006-11-21
then were do i put the script you told me, do i just type in before typing in the automatix ones

---

### Post by taurus on 2006-11-21
Open a terminal, Applications -> Accessories -> Terminal, and type (or cut 'n paste) these lines in!!!

```

echo "deb http://www.getautomatix.com/apt dapper main" | sudo tee -a /etc/apt/sources.list
wget http://www.getautomatix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
sudo apt-get update
sudo apt-get install automatix2

```

---

### Post by arnieboy on 2006-11-21
> **gustav213 said:**
> hey well i wanted to install firefox 2 and read that by installing automix i could get it to work so i went to here website and put the script in the terminal and then it told me to update it and i did and i got this error.


W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C


dont know what it is any help.

just a  heads up: Automatix2 will not update your firefox 1.5.x to 2.0 on Dapper. You will need to be on Edgy to run FF 2.0 (which comes with Edgy by default)

---

### Post by cantormath on 2006-11-21
> **gustav213 said:**
> hey so if i get this right it should look like this right. 

 echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main" | gksudo gedit /etc/apt/sources.list
 wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
 gpg --import key.gpg.asc
 gpg --export --armor 521A9C7C | sudo apt-key add -

and then i do the apt get update and apt get install automatix2. it says it cant be validated bt i just keep on going right. 

thanx a lot,



put the automatix repo in your /etc/sources.list
then in terminal type```

laptop:~$  gpg --import key.gpg.asc
laptop:~$  gpg --export --armor 521A9C7C | sudo apt-key add -
```
should say ok after that
then```

laptop:~$ sudo apt-get update
laptop:~$ sudo apt-get install automatix2
```

then in your application>system menu automatix should be there.

---

### Post by gustav213 on 2006-11-21
yeah i just got it installed, but yeah your right it wont update, so i guess that was kind of stupid, how would i update to 2.0 in 6.06

---

### Post by taurus on 2006-11-21
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by arnieboy on 2006-11-21
> **gustav213 said:**
> yeah i just got it installed, but yeah your right it wont update, so i guess that was kind of stupid, how would i update to 2.0 in 6.06
you cannot actually "upgrade" to 2.0 on 6.06. You can copy the static binaries to a different location like /opt and copy all the plugins to a suitable location. The following is a link but I do not personally endorse the howto itself (so it can cause problems)
[http://ubuntuforums.org/showthread.php?t=283965](http://ubuntuforums.org/showthread.php?t=283965)

---

### Post by arnieboy on 2006-11-21
> **taurus said:**
> [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)
On breezy I had developed a script for installing FF 1.5 and prevent calls to 1.0.x. This should be something similar.

---

