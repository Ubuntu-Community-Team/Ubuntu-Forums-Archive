---
title: "Store JSON Data in local Storage (Java Script)"
date: 2020-09-16
forum: General Help
---

### Post by manpreetweb on 2020-09-16
[LEFT][COLOR=#141414][FONT=Verdana]I am trying to store data in the local Storage from my JSON file. But I am getting an empty array in the local Storage. File name is 'data' in the project.[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana][[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]"friends": [[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]{[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]"id": 0,[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]"name": "Daugherty Gould"[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]},[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]{[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]"id": 1,[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]"name": "Foley Carpenter"[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]},[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]{[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]"id": 2,[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]"name": "Brewer Vinson"[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]}[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]][/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana][/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]localStorage.setItem('firstName',data.friends.name );[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana][/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]I am not getting the right output with above code. How can I get all the names in localstorage.[/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana][/FONT][/COLOR]
[COLOR=#141414][FONT=Verdana]Thank you in advance![/FONT][/COLOR][/LEFT]

---

### Post by norobro on 2020-09-17
You haven't supplied enough code to understand what you are doing. 

Use your browser's "Developer Tools" to see what is wrong.

You have an array of names so if your data is "JSON.parsed()" which "name" do you expect to get with "data.friends.name" 

I think you will have to save the data as one glob and then parse it when you retreive it from localStorage.

---

### Post by manpreetweb on 2020-09-17
I am tring to store the names in localstorage from my JSON file. I am used developer tool, It just says error on line XX and can not access.

---

