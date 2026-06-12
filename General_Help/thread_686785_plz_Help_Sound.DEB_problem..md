---
title: "plz Help Sound/.DEB problem."
date: 2008-02-03
forum: General Help
---

### Post by El_alacran on 2008-02-03
Hello All.
Well I have a Acer aspire 5520 running Ubuntu 7.10 ,32 bit edition and wincrap xp. After a long time I got the video to work thanks to the forums. the sound card in internal i think a realtek HD audio.
anyway after reading a lot  on this great site about getting the sound to work, it seemed really simple. Just go to the packer installer and install the modulus back port, but when I did, it was no place to be found. so I downloaded it and ran it. I gave me this error "dependent is not satisfiable ".

one more thing if I can.
On the wireless, I did this I found on a past post.

tar -xvzf ar5007eg-64-0.2.tar.gz
cd ar5007eg-64-0.2/ar5007eg
sudo ndiswrapper -i net5211.inf
sudo echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
sudo echo 'ndiswrapper' >> /etc/modules 

And I got the net5211.inf to install and the Windows wireless driver program to say yes, but these two commands:

sudo echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
sudo echo 'ndiswrapper' >> /etc/modules 

they both tell me "Permission denied"
I dont know why Plz HELP:( Thanks A Lot

---

### Post by taurus on 2008-02-03
```

udo echo 'blacklist ath_pci' >> **sudo** /etc/modprobe.d/blacklist
sudo echo 'ndiswrapper' >> **sudo** /etc/modules 

```

---

### Post by El_alacran on 2008-02-03
thanks I got it to blacklist but the wireless still doesn't come up in network configuration. I'm confused oh yea I like your signature.

---

