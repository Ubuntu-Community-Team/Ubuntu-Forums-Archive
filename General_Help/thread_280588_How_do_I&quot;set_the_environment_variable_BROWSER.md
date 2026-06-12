---
title: "How do I&quot;set the environment variable BROWSER&quot;?"
date: 2006-10-19
forum: General Help
---

### Post by emarkay on 2006-10-19
One of my installed programs has a Web link button and when I click it, I get this message:

"... set the environment variable BROWSER to the path of your web browser."
OK, and upon typing "env" in Terminal shows no "BROWSER".

I think this data is in the bash_prfile file, correct?  This is the PATH line there:

"# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi"

If I want to add my browser (Seamonkey) to the path I would add:

PATH=$PATH:$HOME/usr/local/seamonkey/seamonkey-bin

Or something like that?
Can anyone help a noob on this?  :)

Thanks!

---

### Post by Zeddicus on 2006-10-19
If you just want to do this on a per user basis, then yes, adding a line to your bash_profile would work (though I believe user customizations generally go in ~/.bashrc).

However, it's not the path that needs to be changed -- just add a line like so:

```
export BROWSER=/usr/local/seamonkey/seamonkey-bin
```

Or wherever the seamonkey-bin executable is.

Then just:

```
source ~/.bash_profile
```

And it should be all set.

---

### Post by devnulljp on 2006-10-19
Or you could add to /etc/environment to make is stick throughout for all users (doesn't export xyz only stick around for the current session?)
Add a line like this to /etc/environment (for a per user basis, add this line  to ~/.bashrc):
```
BROWSER="/path/to/browser/"
```

One good way to set default browser is:```
sudo update-alternatives --config x-www-browser
```

---

### Post by Zeddicus on 2006-10-19
> (doesn't export xyz only stick around for the current session?)

hmm.  I thought it was the opposite.  I have my "editor" variable exported in my .zshrc, and has always worked fine.

But the "sudo update-alternatives --config x-www-browser" sounds like the right "Debian/Ubuntu" way, assuming you want that for *all* users.

I just sorta assumed he doesn't want it for all users because it *looks* like he may have the executable buried in his $HOME.

---

### Post by emarkay on 2006-10-20
If I enter "sudo update-alternatives --config x-www-browser"
I get:
"There is only 1 program which provides x-www-browser
(/usr/bin/firefox). Nothing to configure."

(Ugh, not what I want to see...)

My browser is located here:

Root/usr/local/seamonkey/seamonkey-bin

I'd prefer this to be a global setting, getting SM to be the defauly browser.

(I had to reinstall FF because "YELP" was also disabled by removing FF.)

I didn't know about the "/etc/environment" feature, here's what I have:

"PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_US.UTF-8"
LANGUAGE="en""


Oooh, it's all so new to me... :)

Thanks!

---

### Post by emarkay on 2006-10-21
Anyone want to give me a hand in comfirming what I have?

Thanks.

---

### Post by devnulljp on 2006-10-25
Can you try

sudo update-alternatives --set x-www-browser /usr/local/seamonkey/seamonkey-bin

Or install galternatives <not sure about this, I use KDE>
sudo apt-get install galternatives
sudo galternatives

Scroll to x-www-browser
add the seamonkey path
choose seamonkey radio button

On the command line

update-alternatives --install x-www-browser /etc/alternatives/x-www-browser /usr/local/seamonkey/seamonkey 20

Then, you can use update-alternatives --set x-www-browser /usr/local/seamonkey/seamonkey or update-alternatives --config x-www-browser

---

