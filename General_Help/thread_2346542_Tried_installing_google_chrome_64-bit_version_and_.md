---
title: "Tried installing google chrome 64-bit version and now Kubuntu won't load."
date: 2016-12-16
forum: General Help
---

### Post by swedishmoose on 2016-12-16
Hello,

I am using Kubuntu 16.10.
I made the mistake of trying to install Google Chrome from the .deb file on the Chrome website. I have a 64 bit processor but am currently running the i386 version of Kubuntu. 
I updated my respositories as per [http://askubuntu.com/questions/510056/how-to-install-google-chrome](http://askubuntu.com/questions/510056/how-to-install-google-chrome) and tried the install.
commands used:
get -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -
sudo sh -c 'echo "deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main" >> /etc/apt/sources.list.d/google-chrome.list'

sudo apt-get update 
I ran the .deb in the software installer, and it advised me to run dpkg --add-architechture amd64 in the terminal. I did, and attempted to install the deb again, and the install quit (didn't get any screenshots of that, sorry.)
After the next reboot, Kubuntu dropped to a blinking cursor instead of loading the plasma desktop. I went into single user mode and tried to reverse what I did, but it looks like dpkg is now broken and nothing in /etc/apt/sources.list is working, so I can't install dependencies found in another site, [http://askubuntu.com/questions/79280/how-to-install-chrome-browser-properly-via-command-line](http://askubuntu.com/questions/79280/how-to-install-chrome-browser-properly-via-command-line)
Really all I want at this point is to reverse what I did and go back to using Firefox.
Is there any way I can fix this? Here are some screenshots of the errors:
[IMG]http://i66.tinypic.com/2mms8ew.jpg[/IMG]

[IMG]http://i68.tinypic.com/2w4mqhg.jpg[/IMG]

---

