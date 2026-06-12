---
title: "Navigate to this Directory?"
date: 2007-07-01
forum: General Help
---

### Post by sk8ron on 2007-07-01
I have been trying to install programs from the internet to my computer and it is telling me to 'Navigate to the Directory' with my terminal.  It's then telling me to type in a code and when I do this it says 'bash: ./flashplayer-install: No such file or directory' what am I doing wrong?

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)


That is where I am getting the instructions from.  I can get all the way up to the part where I was  talking about.  What should I do?

---

### Post by cookies on 2007-07-01
Type in a Terminal (Applications > Accessories > Terminal)

cd /path/to/the/folder

so liek this:

/home/YOURUSERNAME/Desktop/flash-folder

then you type

./flashplayer-install

And, isn't Flash available in Synaptic. (System > Administration > Synaptic Package Manager, Go to Settings > Repositories in the program, and then enable all on the first tab, hit close, and then hit Reload, and then search Flash.)

---

### Post by Do0odz on 2007-07-05
> **cookies said:**
> Type in a Terminal (Applications > Accessories > Terminal)

cd /path/to/the/folder

so liek this:

/home/YOURUSERNAME/Desktop/flash-folder

then you type

./flashplayer-install

And, isn't Flash available in Synaptic. (System > Administration > Synaptic Package Manager, Go to Settings > Repositories in the program, and then enable all on the first tab, hit close, and then hit Reload, and then search Flash.)

It doesn't seem to work with me navigating to the directory maybe im doing it wrong ..
after I type /home/MYusername/desktop/flash-folder it still says that there's no such file or directory ..

I have the repos enabled all of them .. and when I search for flash player .. one of the listings is a mozilla plugin gnash .. I installed it and got a problem when I try watching a you tube .. the sound bar stays in the middle of the you tube screen and it blinks .. 

have I downloaded the wrong flash ? ..

---

### Post by Nythain on 2007-07-05
sudo apt-get install flashplugin-nonfree

---

### Post by Do0odz on 2007-07-05
I have tried that before :) many times  and this is what I get 

Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate

---

