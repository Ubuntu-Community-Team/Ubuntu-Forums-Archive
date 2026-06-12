---
title: "devilspie + gnome-terminal issue"
date: 2007-12-28
forum: General Help
---

### Post by dlegend on 2007-12-28
I am currently using devilspie to modify the gnome-terminal on startup with a specific profile but the configuration is not being set on the gnome-terminal for some reason.

I have two startup processes in the session manager -- one "devilspie" and one "gnome-terminal --window-with-profile=DesktopConsole". I have devilspie set with an order of "10" with the "settings" style under current session. The gnome-terminal is default (50 + normal style).

When I login, the gnome-terminal appears but does not inherit the style devilspie specifies. However, when I close the terminal and type in the command "gnome-terminal --window-with-profile=DesktopConsole" via "Run Application", it inherits the style perfectly.

For some reason the terminal retains its decoration when it automatically starts at login but when I close it and open it via run command it will be perfectly how I want it.

My question is, what is causing this and how do I fix it? My thought was that somehow devilspie isn't starting before gnome-terminal (but how would the terminal know the exact location/size to start up in?).

If anyone needs further explaining let me know.

**Edit: Problem Solved**
Interestingly enough, the name of the terminal will default to "username@computer: ~" regardless of what you set in the terminal options if the terminal loads on startup. That is why devilspie was unable to set the configuration for the terminal. Hence my solution:

Modify the profile for "DesktopConsole". Under Title and Command find "Dynamically-set title" -- change that to "Goes after initial title". This will cause the terminal to load with the following title:

> 
username@computer: ~ - username@computer: ~


Since this title is not used by the default terminal profile ("username@computer: ~" is only displayed once in default title), you must modify your .devilspie config with the following (obviously replacing the previous matches statement):

> 
(matches (window_name) "username@computer: ~ - username@computer: ~")


So mine looks like this:

> 
(matches (window_name) "daniel@Se7en: ~ -daniel@Se7en: ~")


I hope this fixes problems for anyone else using devilspie for a built-in desktop terminal.

Here is my whole DesktopConsole.ds (devilspie config) file for reference:

```

(if
          (matches (window_name) "daniel@Se7en: ~ - daniel@Se7en: ~")
          (begin
                    (stick)
                    (below)
                    (undecorate)
                    (skip_pager)
                    (skip_tasklist)
                    (wintype "utility")
                    (geometry "954x100+30+630")
          )
)

```

---

### Post by dlegend on 2007-12-28
After a long of trial and error I found the solution to my problem. I posted the solution at the first post for those who need it. 

Note: The solution only works for single users and you'd have to do multiple matches to specify multiple users unless you use some sort of conditional match expression in the devilspie config.

---

