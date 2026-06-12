---
title: "Can't search or log in to Ubuntu Forums"
date: 2008-04-23
forum: General Help
---

### Post by hamster_billy on 2008-04-23
I can't search and can't log in to this site on my spangly new Hardy RC installation with Firefox 3. I've had to boot up the Gutsy laptop to write this. I haven't done anything daft like turning off cookies.

When I try to log in I type my username and password, press the button, see the 'Thank you for logging in' page, and get forwarded back to the page I was on previously in a logged out state.

Meanwhile when I try to search the forums I get a 'This reCAPTCHA key isn't authorised for the given domain' message, which means I can't type in the random strings, and hence can't search.

Is anyone else finding similar things, or is just me and my nice new Firefox?

---

### Post by jocko on 2008-04-23
I just had a problem which made it impossible to make any new posts, reply to existing posts and edit my previous posts, but I could log in and search.
I found that removing my /home/[COLOR=Gray]username[/COLOR]/.mozilla folder to force firefox to create a new profile fixed it (it's hidden in your home directory, press ctrl+H to see hidden folders in nautilus).
First back up your existing .mozilla folder (or just your /home/[COLOR=Gray]username[/COLOR]/.mozilla/firefox/[COLOR=Gray]somerandomfoldernamehere[/COLOR].default/bookmarks.html to keep your bookmarks).

---

### Post by hamster_billy on 2008-04-23
That worked. Thanks for the suggestion.

---

### Post by hamster_billy on 2008-04-23
don't know how to change the subject to mark thread solved.

---

### Post by jocko on 2008-04-23
I think they lost that function in the forum upgrade last night. They're working on it.

---

