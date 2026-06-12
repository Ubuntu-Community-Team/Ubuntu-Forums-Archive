---
title: "YES/NO option in script"
date: 2014-03-20
forum: General Help
---

### Post by Korkel on 2014-03-20
Hi,

I maked a script to install some programs automatic, but on the end I want an option what shows the option to choose yes or no with the following question: [B]Would you like to reboot the system now? It is recommed.
[/B]
If a user choose no there must be shown a message before something else.
If the user choose yes there must be also a message before something else.

Can someone tell me how?

---

### Post by Dave_L on 2014-03-20
Do you want a command-line solution, or a dialog box?

---

### Post by Korkel on 2014-03-20
In the terminal, that is the command-line right?

---

### Post by Dave_L on 2014-03-20
Yes, so you want the user to type 'y' or 'n'? There are utilities such as zenity that can be used from a terminal script, which display a dialog box with buttons, and return the user's choice to the script.

---

### Post by Korkel on 2014-03-20
> **Dave_L said:**
> Yes, so you want the user to type 'y' or 'n'? There are utilities such as zenity that can be used from a terminal script, which display a dialog box with buttons, and return the user's choice to the script.
Yes. :)

OK, I got on the end this:
```
read -r -p "Druk op [Enter] om verder te gaan..." keyclear
echo "Het word aangeraden het systeem te herstarten...
Typ sudo reboot om te herstarten of exit om de terminal te sluiten."
read input


if [ "$input" == "reboot" ]; then
    sudo reboot
elif [ "$input" == "exit" ]; then
    exit
else
    echo "Dit antwoord is niet gevonden..."


fi

```
When I enter "exit"  the terminal close. When I enter "reboot" the terminal close also but the system doesn't reboot. Also an other answer closes the terminal...

---

