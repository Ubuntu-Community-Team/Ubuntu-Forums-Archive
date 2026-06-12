---
title: "Ekiga Errors"
date: 2006-08-18
forum: General Help
---

### Post by Magellan on 2006-08-18
I was messing around trying to get Ekiga running, then gave up and removed it via Synaptic, then later decided to try again.

I must have done the total removal in Synaptic 'cause it couldn't re-install it.  Apt-get couldn't do it either.

I ended up updating sources.list and running apt-get install ekiga, and that ran fine.  For the most part, it seems to work ok.  I haven't tried a call yet, but it runs and the video and audio all seem to function.

When I start up, I get the following message:
> 
Error while starting the listener for the H.323 protocol

You will not be able to receive incoming H.323 calls. Please check that no other program is already running on the port used by Ekiga.


I am forwarding ports 1720 and 3000-30010 to the pc.

I also get the following message while it is running:
> 
Failed to parse XML file

There was an error while parsing the XML file. Please make sure that it is correctly installed in your system.


any clues?

James

---

