---
title: "Upgrade to 12.10 and Gnome-Sushi no longer works for MP3's"
date: 2013-03-30
forum: General Help
---

### Post by stepheny on 2013-03-30
After upgrading to 12.10 I discovered that Gnome-Sushi no longer allows you to play MP3's. If you press the spacebar a window opens but that's all that happens. All codecs are installed and I can play MP3's with Rhythmbox etc.

This is actually a big deal as when I upgraded to 12.04 the really nice feature whereby one hovered the mouse over a nautilus MP3 file and it played was removed and we had to use Sushi. Now Sushi is broke and there is no way to preview MP3's anymore. 

I hope there is a fix or workaround because I really need an MP3 preview.

---

### Post by stepheny on 2013-03-31
Recently every upgrade has broken something important to me and I am not willing to keep accepting this as normal. It looks like it may be time for me to move to another distro after eight years using Ubuntu. Its a shame but there you are.

---

### Post by stepheny on 2013-03-31
There is a new previewer that works with 12.10. It is called gloobus-preview and the homepage is [here]("http://gloobus.net/gloobus-preview/")  

You need to add a new repository, here are the commands to install it. Remove gnome-sushi completely first.

sudo add-apt-repository ppa:gloobus-dev/gloobus-preview
sudo apt-get update
sudo apt-get install gloobus-preview gloobus-sushi

I will not leave Ubuntu just yet but have to say as a long time user it is not getting better, it is getting worse

Also it would be nice if I could mark this thread as solved. But that is no longer allowed!

---

