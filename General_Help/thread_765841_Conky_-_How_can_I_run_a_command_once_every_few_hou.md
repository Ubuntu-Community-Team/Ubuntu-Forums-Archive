---
title: "Conky - How can I run a command once every few hours?"
date: 2008-04-24
forum: General Help
---

### Post by elmer_42 on 2008-04-24
I am trying to run a command every few hours. I am trying to add an MLB score checker to my desktop. The command in question is posted [here]("http://ubuntuforums.org/showthread.php?t=765763"). Does anybody know of a way to do this?

---

### Post by cammin on 2008-04-25
**$execi** or **$texeci**

If you want to get really fancy. You can make a script that adds conky variables (such as $color) to the text and use
**$execpi** which will then parse the variables. 

Try both **execi** and **texeci** to see which one works better. I'm guessing texeci will, but you never know.

The syntax should be something like...
**${texeci 7200 lynx -nonumbers -dump [http://scores.espn.go.com/mlb/scoreboard](http://scores.espn.go.com/mlb/scoreboard) | egrep -i -A12 -B2 Toronto}**

7200 is the interval in seconds.

---

