---
title: "how do u keep a program running on a remotley controled box?"
date: 2006-11-30
forum: General Help
---

### Post by lime4x4 on 2006-11-30
i have a ubuntu-edgy box next to my tv so i have no monitor,keyboard or mouse.
I remotely control it thru xdmcp.Everytime i start a program it runs but as soon as i close the connection from my main pc the program stops running.
I even tried starting the app after ssh into the box but as soon as i close the screen on my main pc the app shuts down. I don't use vnc cause it's to slow for my liking

---

### Post by halfvolle melk on 2006-11-30
Edit: Doh.
What Ramses said.

Or you could run the command inside **screen**.

---

### Post by Ramses de Norre on 2006-11-30
The '&' operand wont prevent the app from closing when the connection is closed. There is an app though which is exactly created for this purpose: nohup.
So just run the command as: **nohup command** and you can still add the ampersand to put it in the background.

All output from an app ran with nohup will be in ~/nohup.out .

---

### Post by lime4x4 on 2006-11-30
well is there anotherway? I really need to also be able to log back in and c the app running.I record tv shows and i play mp3's thru my sound system which is hooked up to that computer.If i create a playlist and have it start playing then later i want to be able to log back in and change the order or add more songs

---

