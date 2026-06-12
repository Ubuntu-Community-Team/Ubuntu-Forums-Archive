---
title: "Windows Emulators and their limitations"
date: 2006-10-10
forum: General Help
---

### Post by Michael Hopcroft on 2006-10-10
I am hoping to complete my migration to Dapper Drake before Vista and the WGA program become entrenched enough to make the lives of even law-abiding Windows users a living heck. The problem is that there are certain Windows programs that I will still need to use, and for that I would need to use WINE or a similar emulator.

I'm not talking critical professional applications -- those I would never trust to an emulator or similar OS kludge. I am referring to games -- and not the typical MMORPGs that are all the rage now, but specialized simulation games like Matrix Games' wargame The Operational Art of War and the Action! line of PC sports simulations.

Now, here is why I think games of this sort pose a special problem for emulators: they have a very large number of scenarios, seasons, saves, etc. in their packages and the program depends upon the Windows file structure to locate them. A Windows emulator in Linux probably does not create a stable structure that these programs can use. Which would make running these programs under them tricky at best.

So the question is whether there is a way to deal with this short of dual-booting, which has always been a lot of trouble for me in the past.

---

### Post by koshari on 2006-10-10
wine would do the saves, scenarios, ect in a canter, as it creates a phantom c drive and where ever the files are put by the game in a windows systen is precicely where they will be in wine.

---

### Post by 3rdalbum on 2006-10-10
The problem isn't with the Windows filesystem - that part works fine, as the developers can easily find out what a Windows filesystem looks like. The problem is exactly replicating what the Windows libraries do. Because the source code of the libraries is not available for viewing, the WINE developers have to basically guess what happens in them, and then map them to Linux libraries.

If you have lots of games, you might find that some of them work. The older they are, the better the chances that they'll work. If you have an existing Windows partition, you can often get DLLs from there and put them into Wine's fake filesystem to boost Wine's compatibility.

There's also a project by Transgaming, called Cedega, which is more suitable for gaming. You can get their CVS (development) version for free, but you need to compile it yourself, and it doesn't have copy-protection support. Or you can pay them $5 a month for subscription, and get pre-compiled binaries, copy protection support, and the ability to vote for which games you want to see the support for improved.

---

