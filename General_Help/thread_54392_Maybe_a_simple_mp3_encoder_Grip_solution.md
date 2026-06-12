---
title: "Maybe a simple mp3 encoder Grip solution"
date: 2005-08-04
forum: General Help
---

### Post by buster on 2005-08-04
This is intended for all those who have tried almost everything to make Grip encode to mp3s and still get the little message that lame doesn't work. I'm assuming you've already installed software till you are ready to scream.

Do a search and find where Lame is on your computer. (Probably /usr/bin)

Open Grip and go to Encode. Select lame as your encoder. Under this you will see a slot titled "Encoder executable". Change this to point to the executable lame. In my case I changed "lame" to "/usr/bin/lame".

And finally it worked! Apologies to anyone who already wrote this in the forums, but I gave up reading after searching about a billion posts. Found this step at the Grip site itself.

---

### Post by WayneT on 2005-08-04
[QUOTE=buster]This is intended for all those who have tried almost everything to make Grip encode to mp3s and still get the little message that lame doesn't work. I'm assuming you've already installed software till you are ready to scream.

Do a search and find where Lame is on your computer. (Probably /usr/bin)

Open Grip and go to Encode. Select lame as your encoder. Under this you will see a slot titled "Encoder executable". Change this to point to the executable lame. In my case I changed "lame" to "/usr/bin/lame".

And finally it worked! Apologies to anyone who already wrote this in the forums, but I gave up reading after searching about a billion posts. Found this step at the Grip site itself.[/QUOTE]
 My problem is that I do not find a package that contains lame to install (AMD64). Is it in the default? If it is it is the first distro I have found that does.

---

### Post by buster on 2005-08-04
"My problem is that I do not find a package that contains lame to install (AMD64). Is it in the default? If it is it is the first distro I have found that does."

There is much to do if you do not have the software. My solution is just the final step. You may have to add to your repositories to get gstreamer etc. I downloaded what looked like a stable lame deb off the internet and installed with dpkg. Do a search in these forums under headings like mp3, lame, grip etc. Lots of stuff will come up. That's the best place to start.

---

