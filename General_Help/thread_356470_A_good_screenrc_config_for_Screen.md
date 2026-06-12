---
title: "A good screenrc config for Screen"
date: 2007-02-08
forum: General Help
---

### Post by brad.m.sims on 2007-02-08
Most of the ones I could find are poorly commented:
Here is mine

```

#-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-= #

### Created by Brad Sims <tanfj@yahoo.com> 25/06/2004

### I got tired of .screenrc's on the internet being so
### poorly commented... So being a good GNUbie I took matters
### into my own hands; and wrote this dotfile.

# =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-= #

##    Explanation of hardstatus line    ##

# Ignore the ' marks if you use these examples for yourself

# Note that if you want to use the color brown under konsole
# You actually use bright yellow (%{Y}).

# Note the embeded space after the colon, I feel
#  it just looks nicer with a blank between the
#  text and console edge:
#   '%{=b}%{G} Screens: '

# This prints the window listing in blue:
#   '%{b}%w'

# This right-aligns what follows:
#   '%='

# This displays the time (hours and minutes) in 12hr format
# and adds an AM/PM flag, in bold green:
#   '%{G}%C%A'

# This displays the day of the week:
#   '%D'

#This displays the date in Mon/day/year format:
# and again I embeded a space to give me one space
# between the text and console edge:
#  '%M/%d/%Y '

# The resultsing command give you a status line that
#  looks like this:
#   | Screens: 0* bash  <blanks zapped>         5:30PM  Fri, Jun/25/2004 |
#  (The pipes indicate the edges of the xterm/console).

# Green text, time, and date; windows in blue:
hardstatus alwayslastline "%{=b}%{G} Screen(s): %{b}%w %=%{kG}%C%A  %D, %M/%d/%Y "

# =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-= #

##    Some general options    ##

# Turn off start message:
startup_message off

# Set messages timeout to one second:
msgwait 1

# =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-= #

##    Keybindings    ##

# bind <F7> to detach screen from this terminal
# bind <F8> to kill current session
# bind <F10> to create a new screen
# bind <F9> to rename an existing window
# bind <F11> to move to previous window
# bind <F12> to move to next window
bindkey -k k7 detach
bindkey -k k8 kill
# space in keyboard
bindkey -k k; screen
bindkey -k k9 title
bindkey -k F1 prev
bindkey -k F2 next

# =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-= #

```

---

### Post by etank on 2007-02-08
Cool. I will have to try that when I get home later.

---

### Post by ghandi69_ on 2007-02-08
I'm a still a learnin.. but what is the screenrc config for?  And where is located?

---

### Post by brad.m.sims on 2007-02-08
> **ghandi69_ said:**
> I'm a still a learnin.. but what is the screenrc config for?  And where is located?

It is used for GNU Screen, a terminal multiplexer... [http://www.gnu.org/software/screen/]("http://www.gnu.org/software/screen/")

It goes in /home/username/.screenrc

---

### Post by sandeep048 on 2008-05-29
How do i use firefox bindings in screen like ctrl+tab for next and ctrl+shift+tab for previous

---

