---
title: "Time taken by apps to start"
date: 2020-04-05
forum: General Help
---

### Post by amanchesterman on 2020-04-05
This is simply a request for explanation and understanding, it is not a problem to be solved.

I've noticed that when I turn on my laptop, login, and launch the web browser (I'm currently using Chromium) there is a noticeable delay before the browser window appears. I suppose it's only a few seconds - it's not a problem! - but there is a delay while the app loads.

But if I then close the browser, then use a series of other apps for different tasks, and then launch the browser again, the window opens instantly. And it does this as long as the current session is running, until the laptop is turned off.

So it's as though the browser, once started, is waiting somewhere - hidden - ready to reopen instantly whenever it's needed. It's not on screen with the window minimised, but it is ready, and in some sense 'active' and waiting.

I've noted the same behaviour with LibreOffice - which, like Chromium, is a large and complex piece of software. The other apps I use are all rather small and they load quickly even when started for the first time.

Obviously this is a feature of how ubuntu is designed, and it's very clever. But thinking about it has raised some questions in my mind:

1) Where is an app stored while it is waiting and hidden? Is it in the 'swap' partition? 

2) Presumably it is using system resources while it is waiting and hidden? Would the system run raster if the app was totally shut down? (And how would I shut it down completely, anyway?)

3) Is there a way to start the web browser when I turn on the laptop and start the session, but start it in the 'hidden and waiting' state, so that it's instantly ready for use later? (If I add it to the list of 'start up applications' the browser opens with a visible window in the normal way.)

Apologies if these seem idiotic questions to most of you. I'm very much a non-technical (and fairly elderly!) person but I'm curious to understand better how my computer works.

If it matters, I'm using Xubuntu 18.04.4 - but I assume that my question relates to all flavours of Ubuntu ... possibly even to other operating systems as well?

Thanks in advance!

---

### Post by lvm on 2020-04-05
You are observing the effects of disk caching: whenever something it read from a disk it is stored in memory and can be retrieved mush faster the second time provided this memory hasn't been reused for something else.

---

### Post by dragonfly41 on 2020-04-05
As well as the caching issue referred to above, I wonder if the delay after startup is due simply  to your router delay in making network connection when you first startup? Certainly I experience that delay of a few minutes.

Reading this ...

> I'm curious to understand better how my computer works.

and other questions referring to hiding app windows I offer these tips from my own experience in tuning my workflow.

I have multiple apps to startup and I favour using Stacer as my “mission control” GUI.

[https://github.com/oguzhaninan/Stacer](https://github.com/oguzhaninan/Stacer)

The installation commands are:

sudo add-apt-repository ppa:guzhaninan/stacer -y
sudo apt-get update
sudo apt-get install stacer -y

When/if you launch Stacer (there are multiple menu items) explore “Startup Apps”.

Now you can add the apps to startup when to startup your laptop.

Click on “Add Startup App” and you have three fields for each app.

App Name
App Comments
Command


Next, regarding “hiding” apps you can position app windows in a separate Virtual Workspace.

Before embarking on the next steps/tips below perhaps just using Alt+Tab to toggle through windows might be adequate for you?
Try it.


First, to make it easier to understand ,install Docky.

You can do this through Synaptic Package Manager (install synaptic) or simply through command line

sudo apt install docky

You should see the Docky bar at the bottom of your page.

Right click on Docky button (anchor icon) > Settings > Docklets and enable Workspace Switcher.

You might also try enabling Recent Documents and Clippy.

Now in the Docky tray you will see buttons for each open application and docklets.

You can position any docklet button by going back to settings and there is a positioning button for each docklet. For example you might prefer to position Workspaces to the far right.

To place any app in a specific workspace go to its top bar, right click and move its window into another Workspace (thus hiding it).

For example you might have ..

Workspace1 - Desktop only
Workspace2 - Desktop and Chromium browser
Workspace3 - LibreOffice 
and so on .. effectively expanding your mapping of apps to workspaces.

There is a further utility named X-Tile found here.

[https://www.giuspen.com/x-tile/](https://www.giuspen.com/x-tile/)

[http://www.giuspen.com/software/x-tile_3.1-0_all.deb](http://www.giuspen.com/software/x-tile_3.1-0_all.deb)

This allows windows to be organised in each workspace and also map to any virtual Workspace (1 to n in a grid).

Unfortunately the forum has been attacked by spam but the best way of following progress is to install LifeRea and subscribe to the RSS feed.

Another useful tool from the same stable (giuspen) is CherryTree which I use daily. But again forum is infested with spam since giuspen is head down in development and cannot spare time to purge the spam.

Do not be put off by the spam. These two tools are very useful to me in workflow management.

---

### Post by CatKiller on 2020-04-05
The delay for starting them is because those applications are snaps: containerised and sandboxed bundles of the application and the libraries it needs. Slow startup is one of the properties that snaps have. Much has already been said on the pros and cons of snaps, so I won't repeat it here

The reason they start up so quickly the second time is because that file structure that was so laboriously loaded into RAM the first time is still there. It's called file cacheing. Things that you've loaded into RAM stay there in case you find that you need them again. Loading a file into RAM takes exactly the same amount of time if the cells are all zero beforehand as it does when some of the cells have ones in, but reading a file from RAM is orders of magnitude faster than reading it from anywhere else: there is only ever a performance boost from cacheing in this way. It's generally referred to as "empty RAM is wasted RAM."

---

