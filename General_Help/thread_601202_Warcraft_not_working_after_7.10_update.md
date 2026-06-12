---
title: "Warcraft not working after 7.10 update"
date: 2007-11-03
forum: General Help
---

### Post by lferree on 2007-11-03
I had World of Warcraft working great under 7.04 with Beryl.  I suspect it has something to do with the new Compiz in 7.10.

I get "[COLOR="Red"]World of Warcraft was unable to start up 3D acceleration.[/COLOR]" when opening with CrossOver.

Can't get new Wine to work either.

Any ideas?

Thanks.

---

### Post by lferree on 2007-11-05
WoW is working again.  Come to find out, XGL was still loaded from when I was running 7.04.

```
sudo apt-get remove xserver-xgl
```

I can run in both CrossOver and Wine, but I'm still getting very low FPS and my mouse seems to be lagging.

Here's what I have in my WoW Config.wtf file:

```
SET gxApi "opengl"
SET gxWindow "1"
SET ffxDeath "0"
SET gxMultisampleQuality "0.000000"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET shadowLevel "0"
SET alphaLevel "0"
SET trilinear "1"
SET frillDensity "48"
SET farclip "777"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET anisotropic "16"
SET M2UsePixelShaders "1"
SET movie "0"
SET Gamma "1.300000"
SET realmName "Dragonblight"
SET readTOS "1"
SET readEULA "1"
SET SoundVolume "1"
SET MasterVolume "0.69999998807907"
SET gameTip "26"
SET AmbienceVolume "1"
SET uiScale "0.78999996185303"
SET mouseSpeed "1.25"
SET cameraPitchMoveSpeed "90"
SET cameraYawMoveSpeed "180"
SET cameraPitchSmoothSpeed "45"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "2"
SET profanityFilter "0"
SET guildMemberNotify "1"
SET readScanning "-1"
SET readContest "-1"
SET realmList "us.logon.worldofwarcraft.com"
SET useUiScale "1"
SET autoSelfCast "1"
SET UnitNameNPC "1"
SET MusicVolume "0.90000003576279"
SET locale "enUS"
SET soundMaxHardwareChannels "12"
SET SoundSoftwareChannels "128"
SET expansionMovie "0"
SET timingTestError "0"
SET minimapInsideZoom "0"
SET CombatLogRangeParty "2000"
SET CombatLogRangePartyPet "2000"
SET CombatLogRangeFriendlyPlayers "2000"
SET CombatLogRangeFriendlyPlayersPets "2000"
SET CombatLogRangeHostilePlayers "2000"
SET CombatLogRangeHostilePlayersPets "2000"
SET CombatLogRangeCreature "2000"
SET scriptMemory "98304"
SET patchlist "us.version.worldofwarcraft.com"
SET showToolsUI "1"
SET EnableErrorSpeech "0"
SET weatherDensity "3"
SET cameraView "4"
SET EnableMusic "0"
SET coresDetected "2"
SET Sound_VoiceChatInputDriverName "Analog Devices AD1986A"
SET Sound_VoiceChatOutputDriverName "Analog Devices AD1986A"
SET Sound_OutputDriverName "Analog Devices AD1986A"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_EnableErrorSpeech "0"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "1"
SET Sound_AmbienceVolume "1"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET readTerminationWithoutNotice "-1"
SET PushToTalkButton "MiddleButton"
SET checkAddonVersion "0"
SET Sound_ZoneMusicNoDelay "1"
SET Sound_ListenerAtCharacter "0"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x1024"
SET gxCursor "0"
SET accountName "OB1FoShoB"
SET lastCharacterIndex "1"
SET gxMaximize "1"
SET gxMultisample "1"
```

---

