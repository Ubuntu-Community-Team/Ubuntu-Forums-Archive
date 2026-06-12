---
title: "Windows not centered..."
date: 2007-10-18
forum: General Help
---

### Post by chugeniv on 2007-10-18
Hi,

Using the v7.xx of Ubuntu.

Installed from the disk that was sent to me and have all the updates I have been notified of.

For some reason when I open Firefox, or any window on the desktop, they always slightly off center - by about 1/2 inch to the left. Just enough to 'hide' the word 'file' in the top menu bar. I grab the window(s), at the top and shift them to the right. They are now centered.

Nothing on my desktop is off, it just occurs when I open Firefox or some of the  other widows off the desktop: ie. applications>accessories>calculator. But curiously not every single item - maybe 90%.

It's not affecting the computer but it's a hassle.

Thanks,
Bob

---

### Post by omegamike on 2007-10-20
I had the same problem, and it annoyed the heck out of me too. Here is how I fixed it:

1. Crank open a terminal and install the advanced compiz settings manager:

sudo apt-get install compizconfig-settings-manager

2. Click on the Main Menu -> System -> Preferences -> Advanced Desktop Effects Settings

3. On the left side under "Category" click on Window Management

4. Click on "Place Windows"

5. Change the Placement mode to Centered

Hope this helps!

---

### Post by chugeniv on 2007-10-20
Thank you - I appreciate your taking the time to answer.

The problem seems to have been solved but you might not
believe what I did!

I have a relatively new flat panel monitor. I did not like something about
the color so I'm going through the menu that pops up using the monitor
controls. Saw one that said 'auto adjust' or something like that. Pushed 
it and it fixed the problem! Though I don't know why the problem wasn't
there with the previous Ubuntu version.

Next time I will check a few more things first.

Thanks again,
Bob

---

