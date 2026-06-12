---
title: "PPA and Muon"
date: 2017-02-07
forum: General Help
---

### Post by anon_private on 2017-02-07
I have recently updated gimp using a ppa.

I removed the existing gimp using Muon, and installed the new package from the command line (clean install).

Will I be able to update gimp from Muon. I note that it is installed, as  noted by Muon. If not, what is the recommended procedure for updating?

What is the relationship between Muon and a ppa. I note that the ppa is  listed in sources.list.d. I am wondering if Launchpad is linked to Muon?

How can I check that a ppa is secure? I checked the gimp ppa, by  accepting the vailidity of the archive as stated by person of standing  within a graphics community who also uses kubuntu; but, I should be able  to validate myself.

Thank you

---

### Post by ajgreeny on 2017-02-07
All ppa repos such as [https://launchpad.net/~otto-kesselgulasch/+archive/ubuntu/gimp](https://launchpad.net/~otto-kesselgulasch/+archive/ubuntu/gimp) can be both enabled and their security key added to the system by running a command, in the case of that repo ```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
``` after which any updates of packages available in that ppa will be automatic along with all other normal updates.

This assumes muon, which I don't know, works the same as other package managers.

How did you add the ppa to your sources?

I am not sure what you mean when you say that you should be able to validate the ppa yourself; how do you think you can personally validate a ppa?

---

### Post by anon_private on 2017-02-07
Thank you for responding.

I added the ppa using:

sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get install gimp

When I said validate the ppa, I meant insuring the package to download had integrity

I know that the ppa instruction has been included in the sources-list.d folder, but I am not sure how it interacts with Muon. or how it, the ppa, works!

Best wishes

Ps. The surprised icon appeared automatically - it surprised me

I looked for the public key and found none. I also used sudo

gpg  --list-public-keys

---

### Post by deadflowr on 2017-02-07
> I know that the ppa instruction has been included in the sources-list.d folder, but I am not sure how it interacts with Muon. or how it, the ppa, works!
The same way it interacts with the Ubuntu software center or synaptic or the cli apt/apt-get.
muon is no different. It's a frontend to apt. 

> When I said validate the ppa, I meant insuring the package to download had integrity
once you ran that first command, you downloaded the keys that the system uses to validate packages from the ppa archive.
You can run the apt-key command to find your current keys and go to the ppa home page to compare them.
```
apt-key list
```

Also,
And there was really no need to remove gimp.
Once you add a ppa, a simple system update would have upgraded gimp to the new version.

---

### Post by anon_private on 2017-02-07
> **deadflowr said:**
> The same way it interacts with the Ubuntu software center or synaptic or the cli apt/apt-get.
muon is no different. It's a frontend to apt. 


once you ran that first command, you downloaded the keys that the system uses to validate packages from the ppa archive.
You can run the apt-key command to find your current keys and go to the ppa home page to compare them.
```
apt-key list
```

Also,
And there was really no need to remove gimp.
Once you add a ppa, a simple system update would have upgraded gimp to the new version.

i see the keys using apt-key list

I wonder why I did not see any keys using the gpg command: gpg  --list-public-keys.

Before I downloaded the ppa list for gimp, I used muon to download gimp. I don't understand the difference between getting gimp form muon or from the ppa, although the latter is up to date, I wonder why the former is not updated?

---

### Post by deadflowr on 2017-02-07
apt-key and gpg are looking in different places.

apt-key looks for keys pertaining exclusively to apt within the structure of apt and apt's configurations.
those keys are what would be listed in the /etc/apt/trusted.gpg file and the /etc/apt/trusted.gpg.d folder with the folder containing the keys for any added ppas.

gpg looks for keys pertaining exclusively to you as the personal owner/holder of those keys, which are located in your own personal Home folder.
those keys would be listed in the /home/username-here/.gnupg/pubring.gpg file.

If you have never imported or created/exported any keys, from a personal stand point, then you won't see any keys with gpg.
 If that makes sense.

>  I don't understand the difference between getting gimp form muon or from the ppa, although the latter is up to date, I wonder why the former is not updated?

configuration issues?
does it stay the same if you run muon's check for updates feature?
(Or does that feature no longer exist in kde5?)

---

