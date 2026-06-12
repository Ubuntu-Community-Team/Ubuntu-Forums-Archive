---
title: "Problems Installing Sofware Via PPA 16.04"
date: 2016-05-15
forum: General Help
---

### Post by jooge on 2016-05-15
Hi folks,

I have run into an issue when installing some software/apps via PPA. I just installed 16.04 and several (most ) of the software/apps when I install them I gets this. How can I fix this?


```
W: The repository 'http://ppa.launchpad.net/tualatrix/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 3B068FB4789ABE4AEFA3BB491397BC53640DB551 uses weak digest algorithm (SHA1)
E: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/xenial/main/binary-i386/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by RobGoss on 2016-05-15
Hello and welcome, Go to **>** **Software & Updates**, choose **> ** **Other Software **you will see a list of PPA's there it looks like the following maybe outdated or not found

> [COLOR=#000000][FONT=Ubuntu Mono]E: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]E: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/xenial/main/binary-i386/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/xenial/main/binary-i386/Packages)  404  Not Found[/FONT][/COLOR]

Just check those with the errors and remove them, then save any changes and exit.....

---

### Post by PaulW2U on 2016-05-15
> **jooge said:**
> Hi folks,

I have run into an issue when installing some software/apps via PPA. I just installed 16.04 and several (most ) of the software/apps when I install them I gets this. How can I fix this?
Further to what RobGoss has said, the Google related lines are just warnings and can be ignored (for now). I understand that Google are working to update their repositories so that the warnings will no longer be shown.

It seems that you have added the PPA for Ubuntu Tweak which is no longer being maintained by its author - [Ubuntu Tweak Is Now Officially Dead and Buried]("http://news.softpedia.com/news/ubuntu-tweak-is-now-officially-dead-and-buried-503672.shtml"). unity-tweak-tool, available in the official Ubuntu repositories will probably do most of what Ubuntu Tweak could do, may be more.

---

### Post by jooge on 2016-05-15
Thank you for the info PaulW2.

RobGoss, I actually dont see those 2 packages that you mentioned. Thi is all I have in "Other Software"


[[IMG]http://8.t.imgbox.com/XanapvXx.jpg[/IMG]]("http://imgbox.com/XanapvXx")

---

### Post by deadflowr on 2016-05-15
Fourth ppa listed from the bottom in the screenshot.

covers both amd64 and i386 packages for the tualatrix ppa.

Simply uncheck it to disable.

---

### Post by RobGoss on 2016-05-15
> **jooge said:**
> Thank you for the info PaulW2.

RobGoss, I actually dont see those 2 packages that you mentioned. Thi is all I have in "Other Software"


[[IMG]http://8.t.imgbox.com/XanapvXx.jpg[/IMG]]("http://imgbox.com/XanapvXx")


They were listed in your first post I just copied them to show you what needed to be removed.

---

### Post by jooge on 2016-05-15
Doh!! My bad. Thanks again fellas for your help.

Take care :)

---

