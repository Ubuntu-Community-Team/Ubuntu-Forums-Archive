---
title: "F.E.A.R. Dedicated Server Help"
date: 2007-07-04
forum: General Help
---

### Post by OpticalIllusion on 2007-07-04
I really don't know where else to turn with this one.  I was wondering if anyone here has experience with running the F.E.A.R. dedicated server on Linux.  

The problem I'm having is with Server Options.  I made a server options list which looks like this:
```


[ServerSettings]
GameType=DeathMatch
ServerMessage=
UsePassword=0
Password=password
AllowScmdCommands=1
ScmdPassword=**********
Port=27888
BindToAddr=
BandwidthServer=3
BandwidthServerCustom=1500
LANOnly=0
Dedicated=1
AllowContentDownload=0
MaxDownloadRatePerClient=40960
MaxDownloadRateAllClients=655360
MaxSimultaneousDownloads=16
MaxDownloadSize=-1
RedirectURLs=
ContentDownloadMessage=
EnableScoringLog=0
MaxScoringLogFileAge=0
AllowVoteKick=1
AllowVoteTeamKick=1
AllowVoteBan=1
AllowVoteNextRound=1
AllowVoteNextMap=1
AllowVoteSelectMap=1
MinPlayersForVote=5
MinPlayersForTeamVote=3
VoteLifetime=30
VoteBanDuration=60
VoteDelay=0
UsePunkBuster=1
[DeathMatch]
BriefingOverrideMessage=
RunSpeed=1.5
SessionName=*******
ScoreLimit=250
TimeLimit=15
NumRounds=2
MaxPlayers=10
UseWeaponRestrictions=1
RestrictedWeapons=Cannon,Missile Launcher,Plasma weapon,
RestrictedGear=
EndRoundMessageTime=5
EndRoundScoreScreenTime=10
Mission0=Worlds\ReleaseMultiplayer\Cafeteria
Mission1=Worlds\ReleaseMultiplayer\Campus
Mission2=Worlds\ReleaseMultiplayer\Construction
Mission3=Worlds\ReleaseMultiplayer\Docks
Mission4=Worlds\ReleaseMultiplayer\Evac
Mission5=Worlds\ReleaseMultiplayer\Factory
Mission6=Worlds\ReleaseMultiplayer\HighTech
Mission7=Worlds\ReleaseMultiplayer\Office
Mission8=Worlds\ReleaseMultiplayer\Refinery

```

Now, to specify that I want to use my own server options, I named that file **options1.txt** and put it in the ServerOptions folder.  Next, I edited the **start.sh** script to look like this:

```

#!/bin/sh
export LD_LIBRARY_PATH=$PWD:$LD_LIBRARY_PATH
./fearserver.bin -optionsfile options1

```

When I start the server using ./start.sh, it loads all the default settings anyway.  I can't seem to figure it out.

---

### Post by OpticalIllusion on 2007-07-04
bump

---

