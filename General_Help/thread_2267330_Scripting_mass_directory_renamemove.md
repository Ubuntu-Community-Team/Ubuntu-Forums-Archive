---
title: "Scripting mass directory rename/move"
date: 2015-02-28
forum: General Help
---

### Post by Derek Karpinski on 2015-02-28
Sample tree of my current music folder:

```

&#9500;&#9472;&#9472; Albert King - Born Under a Bad Sign
&#9474;   &#9500;&#9472;&#9472; 01 Born Under A Bad Sign.m4a
&#9474;   &#9500;&#9472;&#9472; 02 Crosscut Saw.m4a
&#9474;   &#9500;&#9472;&#9472; 03 Kansas City.m4a
&#9474;   &#9500;&#9472;&#9472; 04 Oh, Pretty Woman.m4a
&#9474;   &#9500;&#9472;&#9472; 05 Down Don't Bother Me.m4a
&#9474;   &#9500;&#9472;&#9472; 06 The Hunter.m4a
&#9474;   &#9500;&#9472;&#9472; 07 I Almost Lost My Mind.m4a
&#9474;   &#9500;&#9472;&#9472; 08 Personal Manager.m4a
&#9474;   &#9500;&#9472;&#9472; 09 Laundromat Blues.m4a
&#9474;   &#9500;&#9472;&#9472; 10 As The Years Go Passing By.m4a
&#9474;   &#9500;&#9472;&#9472; 11 The Very Thought Of You.m4a
&#9474;   &#9492;&#9472;&#9472; Cover
&#9474;       &#9492;&#9472;&#9472; 499.png
&#9500;&#9472;&#9472; Various Artists - Nuggets - Original Artyfacts from the First Psychedelic Era 1965 - 1968
&#9474;   &#9500;&#9472;&#9472; CD1
&#9474;   &#9474;   &#9500;&#9472;&#9472; 01 I Had Too Much To Dream (Last Night).m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 02 Dirty Water.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 03 Night Time.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 04 Lies.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 05 Respect.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 06 A Public Execution.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 07 No Time Like The Right Time.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 08 Oh Yeah.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 09 Pushin' Too Hard.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 10 Moulty.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 11 Don't Look Back.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 12 An Invitation To Cry.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 13 Liar, Liar.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 14 You're Gonna Miss Me.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 15 Psychotic Reaction.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 16 Hey Joe.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 17 Romeo & Juliet.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 18 Sugar And Spice.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 19 Baby Please Don't Go.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 20 Tobacco Road.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 21 Let's Talk About Girls.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 22 Sit Down, I Think I Love You.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 23 Run, Run, Run.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 24 My World Fell Down.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 25 Open My Eyes.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 26 Farmer John.m4a
&#9474;   &#9474;   &#9500;&#9472;&#9472; 27 It's-A-Happening.m4a
&#9474;   &#9474;   &#9492;&#9472;&#9472; Cover
&#9474;   &#9474;       &#9492;&#9472;&#9472; 196-1.png

```

I want to change to:
Artist/Album/tracks

I have 100's of folders to rename.

I need to parse each line: Albert King - Born Under a Bad Sign and split it, and mkdir 'Born Under a Bad Sign' under Albert King.  I'm having issues parsing the line.  Awk got me close, but I got an extra whitespace in front.  Notice '1965 - 1968' contains a ' - ' which I was using for splitting.

Any ideas?

Edit: No access to GUI on media server.

---

