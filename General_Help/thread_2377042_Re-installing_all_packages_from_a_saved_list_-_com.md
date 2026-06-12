---
title: "Re-installing all packages from a saved list - comments please."
date: 2017-11-08
forum: General Help
---

### Post by makem2 on 2017-11-08
When I install the system I always make a separate /home partition. When I need to re-install for some reason such as a failed update I usually re-install each previously installed package as and when I need to use it. It occurred to me that by doing that I was leaving parts of software in /home which the system may attempt to start.

After a recent install I had a number of problems which have been solved except for a one involving plymouth which could have been caused by this 'left over' data.

I have come across guidance about saving a list of installed packages (see below) and upon a reinstall, reinstalling all packages using that saved list.

My question is: Would re-installing the previously installed packages from an apparently happy working installation (before it went wrong), avoid having problems with the new install?

I ask this because a number of default packages are installed during a re-install so these would be overwritten by those from the saved list so maybe that could cause a problem?

I would be grateful for comments on the pros and cons of taking this route in the future.

Instructions:

To save the list of installed software use following command:

sudo dpkg --get-selections > packages_list

Then when you reinstall ubuntu on your machine you can use the following commands to install all the packages:

(first copy the packages list to ~/makem) (My username)

sudo dpkg --set-selections < packages_list

This command does not install them, so:

sudo apt-get -u dselect-upgrade

System will now download and install all the packages.

(I cannot find the source of these instructions now)

---

### Post by #&amp;thj^% on 2017-11-08
Hi makem2...Backing up a home partition has become a little different these days, and if I'm not mistaken you once had 17.10 installed>>correct? (Did you copy this Home partition?)
I have the luxury of having many hard rives that I use in testing and my production Boxes.
So I have 1.A clean Home (Virgin if you will) with nearly a factory install (Just the basics multimedia and Browsers) That is my Home that copy to my Newer Installs.
Now on my production Machine's i will back-up all the software that I have installed.
My method goes like this:
A slight variation on Installing packages by importing the list with dpkg --set-selections should do the trick.

Save the list of packages on your reference system:
**Should be root to complete with no errors**
This below code can be run without Root...Thanks to deadflowr for making me make that clear!:)
```
dpkg --get-selections > packages.lst
```

Then install packages based on that list on your target system, after updating the source list of available packages:

```
dpkg --merge-avail <(apt-cache dumpavail)
dpkg --clear-selections
dpkg --set-selections < packages.lst
apt-get dselect-upgrade
```

So First, retrieve the list of packages installed on the machine which will serve as the &#8220;model&#8221; to copy.

 ```
dpkg --get-selections > pkg-list
```

Then In the new machine:
Update dpkg's database of known packages

```
 avail=`mktemp`
 apt-cache dumpavail > "$avail"
 dpkg --merge-avail "$avail"
 rm -f "$avail"
```

Update dpkg's selections

```
dpkg --set-selections < pkg-list
```

Now we apt-get to install the selected packages

```
apt-get dselect-upgrade
```

This works for me. Hope it helps and dose not add new confusion.
Sometimes I have to clear specific Packages in **.cache **&&** .config**

---

### Post by deadflowr on 2017-11-08
> I ask this because a number of default packages are installed during a re-install so these would be overwritten by those from the saved list so maybe that could cause a problem?
No, not a problem.
Only packages that have new updates would be overwritten, anything installed with it's latest version would (or should ) simply be ignored.
> My question is: Would re-installing the previously installed packages from an apparently happy working installation (before it went wrong), avoid having problems with the new install?
That would really depend upon what the problem was.

Also this command
```
sudo dpkg --get-selections > packages_list
```
can be run without sudo, since it's writing to your own home folder and not to the system folders, like /etc/apt or what have you

---

### Post by makem2 on 2017-11-08
Hi 1fallen, yes I did have an install of 17.01 which was updated to 17.04 but prior to that I had saved a package list from the 16.04 which was running fine. It had many packages installed over the period of maybe a year or more when I made this list.

Having the problems with 17.04, I decided to return for the time being to 16.04 and started installing some of the previously installed packages I needed quite soon. Later, I began to wonder if I should have put the old stuff back on immediately after the reinstall because I now had a /home with a mixture of stuff from 16.04 and 17.01 and 17.04! (maybe).

Like you, in Windows I kept a pristine install with drivers etc for new installs. I have never done this with xubuntu. So, I am wondering what the repercussions maybe if at this late stage, I drop all the old package back on. The stuff from the 17's will still be there so really I cannot see any advantage now. It is to late in my opinion.

What it really needs is a 'good' copy of /home being dropped in to fully replace the existing /home as far as I can see. I could do this in windows buy having a basic install running alongside the main one plus a pristine set up windows which I could drop in from the basic install to replace the corrupt main windows.

Reinstalling previous packages would not do that.

---

### Post by makem2 on 2017-11-08
> **deadflowr said:**
> No, not a problem.
Only packages that have new updates would be overwritten, anything installed with it's latest version would (or should ) simply be ignored.

That would really depend upon what the problem was.

Also this command
```
sudo dpkg --get-selections > packages_list
```
can be run without sudo, since it's writing to your own home folder and not to the system folders, like /etc/apt or what have you

Nice to know that only updated software would be overwritten. 

The problem is/would be, that I do not know what the problem is/would be. The more I think about it other that saving time and effort, reinstalling previous packages could not be relied on to fix a problem, especially in my recent case.

What about this instead?

Keep an rsync copy of /home somewhere else and using a live USB, replace the contents of /home totally, then, reinstall all packages from the list?

Care would need to be taken that the drive layout was identical in both installs.

In my case I make a regular rsync backup of everything on my SSD and 1TB windows and data HD to remote storage. If what I suggest would work luckily I have not copied the data to the second backup HD yet so have copies of both the old and the new (current) /home.

---

