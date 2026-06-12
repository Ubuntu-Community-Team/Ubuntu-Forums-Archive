---
title: "Having problems downloading some packages via Synaptic"
date: 2012-10-21
forum: General Help
---

### Post by oxf on 2012-10-21
I'm having some major problems downloading some packages in Synaptic. The packages concerned are all QGIS (Quantum GIS mapping software) but this issue could potentially apply to anything.

Problem 1:
When I downloaded and installed QGIS on my other PC it downloaded about 40 packages which makes sense. Now when I try and do it on this laptop Synaptic only lists two neither of which are the main  QGIS package.

Problem 2:
I checked that the repositories were added and they were. I then tried to get them via the terminal and the apt-get command. When I did that it told me this:

```
Reading package lists... Done
W: GPG error: http://qgis.org precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EBB1B7ED997D3880
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/InRelease

```
This implies my problem might be that the public key has not been added. Ok I have the public key provided by the QGIS but I cant see how to enter that in Synaptic. It gives me an option to import a file  but I don't have a file, I just have the key as listed on the website. How do I enter in? This might solve my problem so I'll leave it there for now.

Please someone help me!

Thanks
Veronica

---

### Post by CaptainMark on 2012-10-21
This is for an older version but it should still apply [http://www.thegeekstuff.com/2009/05/apt-get-update-how-to-solve-no-public-key-available/](http://www.thegeekstuff.com/2009/05/apt-get-update-how-to-solve-no-public-key-available/)

---

### Post by oxf on 2012-10-22
> **CaptainMark said:**
> This is for an older version but it should still apply [http://www.thegeekstuff.com/2009/05/apt-get-update-how-to-solve-no-public-key-available/](http://www.thegeekstuff.com/2009/05/apt-get-update-how-to-solve-no-public-key-available/)

Yes thank you, that did it!
What I don't understand though is why after I added it synaptic still didn't show the packages but I could get them using the terminal and apt-get?
Anyway thanks..

---

### Post by CaptainMark on 2012-10-22
Your welcome

---

