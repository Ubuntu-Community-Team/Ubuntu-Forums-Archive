---
title: "Spotify for Linux"
date: 2013-02-10
forum: General Help
---

### Post by jockyburns on 2013-02-10
I'm trying to install Spotify for Linux on my machine. Here's the instructions off their website
> Debian
# 1. Add this line to your list of repositories by
#    editing your /etc/apt/sources.list
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free

# 2. If you want to verify the downloaded packages,
#    you will need to add our public key
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59

# 3. Run apt-get update
sudo apt-get update

# 4. Install spotify!
sudo apt-get install spotify-client


I can't edit the /etc/apt/sources.list,,, as my machine tells me I don't have permission to do so. My computer is set to automatically log me in on startup. So is it possible to edit the sources.list using gedit, or do I have to do it all through the terminal ??
BTW, I'm running 12.04 LTS

---

### Post by Yellow Pasque on 2013-02-10
To edit a file with root permissions, you can use:
```
gksu gedit <file>
```

However, it's probably easier/safer to use apt-add-repository:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59
sudo apt-add-repository "deb http://repository.spotify.com stable non-free"
sudo apt-get update
sudo apt-get install spotify-client
```

---

### Post by jockyburns on 2013-02-10
Thankyou so much Temüjin... Now done. ;);)

---

