---
title: "script/hotkey type of program for an arcade machine."
date: 2015-01-05
forum: General Help
---

### Post by buttonmasher2 on 2015-01-05
The game is called Mad Bomber. It's available in the Software Center. 
Or here:[  http://www.newbreedsoftware.com/madbomber/download]("http://www.newbreedsoftware.com/madbomber/download")

It's a clone of the old Atari game Kaboom! 



The goal is to build an arcade machine with this game that has a control panel consisting of only 1 spinner and 1 button. Nothing else.


Once you launch the game, a screen loads with options. One player game - Two player game - Options - High Score - etc... It starts with the One Player game highlighted so all you have to do is press the Fire button. Perfect!. After your game is over, it asks you to press Escape which then brings you back to the beginning menu. Which wouldn't be a problem if that's all it did. Pressing Escape during a game will also bring you back to the beginning menu. If you press it on the beginning screen, it quits the game. Folks tend to hit all the buttons all the time on arcade machines. So having a dedicated Esc button is out of the question. 

Here's the original Beginning Screen.
[IMG]http://www.newbreedsoftware.com/madbomber/screenshots/title.gif[/IMG]

Here's the original game screen
[IMG]http://www.newbreedsoftware.com/madbomber/screenshots/game.gif[/IMG]





I've pretty much got it all sorted out now. It works with 1 spinner and 1 button, in Windows. I've replaced all the ingame images and sounds with the original media so it's more like the classic game.

Here's the new Beginning Screen, press Spacebar to start a game. All the options are there but you only see then when they're selected. And with only a spinner and 1 button, that can't happen.  ;D

[[IMG]http://i.imgur.com/1NFreNY.jpg[/IMG]]("http://i.imgur.com/1NFreNY.jpg")


Here's the ingame Start Screen, the little text blinks before each round. Press Spacebar to start round.

[URL="http://i.imgur.com/lCeG2mk.jpg"][IMG]http://i.imgur.com/lCeG2mk.jpg</a>[/IMG]





[IMG]http://i.imgur.com/WrjswN8.jpg[/IMG]
[/URL]Here's the Game Over Screen

I made a script that changes the action of the Spacebar. It looks for that specific darker green color only found on the Game Over screen. If it finds that color, it will act as the Esc key which will restart the game. If it doesn't find that darker green color, it'll just act as the Spacebar which will start a new game and rounds like usual. 

```
Space::
PixelGetColor,Color,320,240
If Color=0x005C31
{
Space::Esc
return
}
```

That's the part I need to work on Lubuntu. I don't know if there's a similar program to AHK, I've found AutoKey but I don't think it can grab a specific pixel color and go from there the way I've got it set up. And I know nothing about Python.

Here's a gameplay video if you're interested. I sped up a good portion of the video to get to the 1000 mark so you can here the "One Up" sound effect. Again, it needs to be dropped a couple of db. But you get the idea. Let it run at least :40 to hear all the sounds. Sorry the quality of the video bites. I'm trying a new capture program and I hardly know what the hell I'm doing. 

[http://www.youtube.com/watch?v=Ae5ZOYzQbkM](http://www.youtube.com/watch?v=Ae5ZOYzQbkM)




Is there a way to get the Spacebar or a mouse button to do the same action as the AHK script? Or if you know of another way to achieve the goal of having only a spinner and 1 button on a control panel and run this game, I'm all ears.

---

