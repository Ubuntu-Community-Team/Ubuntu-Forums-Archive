---
title: "Can &quot;Failed to send host log message&quot; be resolved?"
date: 2023-06-24
forum: General Help
---

### Post by tommyluciano on 2023-06-24
Hello, new to the forums, not that new to Ubuntu.

I would like to start by saying that I am sorry if this is an annoying question that you get a lot, and understand that "Failed to send host log message" is not an error that will break the OS in any way and is not really an issue since upon booting it just moves past the message anyway. First and foremost, I am interested in exactly what it is that causes this message to appear. I have tried to figure it out myself by going through a lot of files with the **sudo visudo FileName **command but so far have no found any references to this specific message. Secondly I would like to know if there is any way to stop this message from appearing (hopefully speeding up boot time.) I know one or two things about Ubuntu, as I have been using different flavors of Ubuntu for a few years, I am however no expert, and I know that there are people within the community who know a lot more about it than I do. Normally I would name the distro that I am using but since I am not sure whether or not naming this particular Ubuntu-based disro is frowned upon, I choose to leave out the name, but it is as mentioned Ubuntu-based.

If anybody can give me any information I would greatly appreciate it, especially more technical information about why this "Failed to send host log message" appears when booting.

Thanks for taking the time to read my post!

All the best to you :D

---

### Post by Rubi1200 on 2023-06-25
Hi and welcome to the forums :-)

Firstly, I would seriously recommend **not** going through files using sudo unless you intend editing them. One mistake in error and you could really mess things up. Use the **cat **command to view file contents instead.

If you boot using recovery mode do you also get this message?

Are you using a VM?

---

