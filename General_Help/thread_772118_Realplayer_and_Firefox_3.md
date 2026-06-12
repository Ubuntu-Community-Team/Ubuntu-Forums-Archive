---
title: "Realplayer and Firefox 3"
date: 2008-04-28
forum: General Help
---

### Post by harambe on 2008-04-28
Having searched through many postings and taken action accordingly, I still can't get Firefox 3 to stop using Totem to play streamed .ram files.

So, I tried using SeaMonkey to run these files and it works fine - which to me indicates the issue must lie in Firefox 3 ( or its settings ) somewhere.

Anyway - my solution for all those trying to "Listen Again" to the BBC - use SeaMonkey - keep FireFox 3 for the rest of the WEB.

---

### Post by 5735guy on 2008-04-29
Here is how you get Real Player streaming on Firefox 3 with Hardy.

Download Real Player 11 [http://www.real.com/linux](http://www.real.com/linux)

Open a Terminal and submit the following commands.

cd ~/Desktop 

chmod +x RealPlayer11GOLD.bin

sudo ./RealPlayer11GOLD.bin

Real Player 11 will then install.

Go to a Real streaming website ie BBC Radio [http://www.bbc.co.uk/radio/](http://www.bbc.co.uk/radio/)

Select a station you would like to listen to and click Listen Live, a message will then appear asking you to install missing plugins, click on that then select and install the Helix option at the bottom.
Restart Firefox once the software is installed and thats it you are ready to go.It works with Listen Again as well.

IMPORTANT
Uninstall any conflicting packages first ie. Mozilla Mplayer, Totem Mozilla, Gecko Media Player and Gnome Player.

ENJOY. :guitar:

---

