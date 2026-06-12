---
title: "Unzipping large file"
date: 2020-09-24
forum: General Help
---

### Post by sks24 on 2020-09-24
I Downloaded all my Google data, and *I think* that what I would like to do is open up the zip files on the external drive on which the download is located. But I'm having trouble navigating to the file in the terminal, and I thought I would ask for advice here before going any further. To begin, [here's a shot of the download showing the path]("https://photos.app.goo.gl/jTLkfq95P5jUTHqz9"). It consists of six files, and all but two of them are 50 GB. (The odd two are much smaller in size.) 

[And here's me struggling with the file path]("https://photos.app.goo.gl/4cuLxodxHtqhUqy98"). I've never done much in terminals, so there's a lot I heven't learned. But I really need some hand-holding here because I feel there's a lot I don't know here.

I have no idea how Google slices up thee downloads, so for now I'm thinking the thing to do is just open them up in a folder in my 4TB external drive. I'm only doing this so that I can know how it's done in case I ever did lose my account. (Although that has never happened, and I've had the account since @2007.)  But, you know, just in case. 

Anyway, if there's a GUI way to do this that would be great, but I'm thinking not. And if there's a better way to do this than how I'm doing it then please advise. 

Thanks,
Scott

---

### Post by CatKiller on 2020-09-24
> **sks24 said:**
> And here's me struggling with the file path. 

So, a couple of things: case is important, which you probably already know. / is a directory (the root directory of the filesystem tree), so /scott would be a subdirectory of that root directory; scott (or ./scott, which means the same thing, since . means, "the directory I'm in now") would be what you were after at that point. Ambiguous characters, like space, can be "escaped" using the \ character, meaning that the shell shouldn't try to interpret them. 

But, most importantly, you can use **Tab-completion**. Type the first couple of letters of a command or path, remembering that case is important, and then press Tab. The shell will fill in as much of the rest as it can; type another couple of letters and press Tab again. If there's more than one way to complete what you've got, pressing Tab twice will give you a list. 

> Anyway, if there's a GUI way to do this that would be great, but I'm thinking not. 

I think most desktop environments come with a GUI utility that can handle zip files. I just right-click on them and pick Extract Here. And it does.

---

### Post by scorp123 on 2020-09-24
> **sks24 said:**
>  [And here's me struggling with the file path]("https://photos.app.goo.gl/4cuLxodxHtqhUqy98"). 

You either have to escape the spaces ....
```

cd /path/To\ a\ Place/with/Spaces/in/the/name

```

... or you use quotation marks ...
```

cd "/path/To a Place with Spaces/in/the/name"

```

... or you go into "lazy mode" and just start typing the beginning of the path name but then hit the TAB key and let the shell auto-complete it for you:
```

cd /path/To <press TAB>

```

The terminal should be able to resolve the path you started typing and autocomplete it correctly.


Also: since you seem to have a file manager on your system you could also use that file manager's ability to unpack archive files. It's not like the terminal "must be used at all costs" to achieve what you want in your case.

---

