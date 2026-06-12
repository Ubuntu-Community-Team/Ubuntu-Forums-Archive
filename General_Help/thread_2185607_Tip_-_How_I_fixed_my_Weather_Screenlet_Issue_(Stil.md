---
title: "Tip - How I fixed my Weather Screenlet Issue (Still works on Saucy)"
date: 2013-11-03
forum: General Help
---

### Post by Mike3 on 2013-11-03
Well, first I must say that I recommend installing not from the stable  screenlets PPA, but the development one found here. You know the drill -  add from Software Sources or Software and Updates (whatever Canonical  has decided to change the name to):

[HTML]https://launchpad.net/~screenlets-dev/+archive/ppa[/HTML]
To quickly add it: ```
ppa:screenlets-dev/ppa
```

Then, at least on Saucy it should automatically ask you to refrsh to software sources - if not, just run this from the terminal:
```
sudo apt-get update
```

Also, of course, install all your screenlets from the terminal
```
sudo apt-get install screenlets-pack-all
```

Make  sure you go into "Software Sources" and change the automatic behavior  that makes your distro your actual distro to the highest possible one,  which is Quantal. Unless of course you are running Precise or something  older, then you can just leave it as is for this part. But if you're  running Raring or Saucy change it to Quantal. It's worked well enough  for me. This is because there are no dedicated repositories for Raring,  Saucy, or Trusty (the development branch) as of the time I'm writing  this.

Yes I've been using this PPA for quite some time, as well  as the screenlets. Why not the stable PPA? It gave me issues and I  remember having to always restart the screenlets about once a day, and  plus the stable PPA only works up to Precise, and it may even have  issues there. I haven't tested it, and I like to run stable,  non-development software myself, but sometimes the stable branch hasn't  been updated in ages to the point development is more stable ironically  enough.

You're not done yet. If you want the Clearweather screenlet to work, you need to install a different version than the one that comes from the PPA. Why? It may work or give a different issue elsewhere, but I live in the United States, and when I enter in my Zip Code, it will give the wrong town/city. With this one from GNOME look, everything works as expected. Also, the one included in the PPA loves to shuffle around the days of the week as of late, and it literally included duplicate days out of order! Have no fear, a manual install from [here]("http://gnome-look.org/content/show.php/ClearWeather?content=120208/") will fix these issues. Download and save that ClearWeather screenlet.

How to manually install, you ask? Search for and open up the screenlets manager in the dash (it is simply called "Screenlets" without quotes). Once you open it, you should see a window and hopefully a new icon in the tray. If you cannot see this icon, uncheck/check the checkbox next to "Show daemon in tray" until you do. Then, you click the "Install" button in the left column of the window, and "OK" (we're just installing a screenlet). Then go to the download location and double click it or just select it and click "Open". Click yes to any prompts that come up. Now, for good measure you can always restart all your screenlets from the menu in the screenlet daemon's tray icon, just to be safe. Now you should be able to configure your screenlet without issues.

---

