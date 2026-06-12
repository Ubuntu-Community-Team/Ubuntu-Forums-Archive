---
title: "Issues with Xubuntu 14.04 on Chromebook with Crouton"
date: 2015-06-25
forum: General Help
---

### Post by tessk2 on 2015-06-25
When I install Xubuntu 14.04 through Crouton, it does not look exactly the same as the version on my desktop which I download directly from the Xubuntu website. The Application manager is different, and some default actions are different. And when I try to install programs, I get different problems. Whats the difference between the two?

Biggest problem is that I cannot get Dropbox to install. It worked fine on my last install of Xubuntu on this Chromebook (C720). I deleted the chroot and re-installed, and things have not been right since. I downloaded the .deb from the Dropbox website, and I try to install it. It says that it is installed, and I get a listing in my Applications menu, but it does not work. I click on it and nothing happens. I have completely removed it several times and re-installed it, with no effect. 
EDIT: wow I randomly decided to try Dropbox on the terminal again, entered "dropbox start" and now it works all of a sudden. I had done this a thousand times before, no clue why it is working now.

Other issue is that I cannot get the panel icon for Redshift to display. I have redshift-gtk installed and it set itself an Autostart entry which I have amended with location settings. It runs on boot like its supposed to but the icon is not present. 

I was thinking that maybe I am just missing an entry in my panel to display the icons for both Dropbox and Redshift; I thought the required item was "Indicator Icons" or something like that, but I do not have anything of the sort listed as possible items to add to the panel. 

Any ideas? I have been Googling these issues forever, and have yet to find any solutions.

EDIT2: Looks like I was right, I was missing the Indicator Plugin to show application icons in the panel. After installing xfce4-indicator-plugin, redshift icon is displaying. I think its odd that the Dropbox icon displays in the notification area, while redshift is in the Indicator area..


Also I somehow changed a setting to use a "Dark" theme for the entire desktop. Its nice that window borders and such are black, but text boxes are also black, so for a  lot of text boxes its impossible to read the text you are entering. But it only happens with some text boxes and not others.

---

