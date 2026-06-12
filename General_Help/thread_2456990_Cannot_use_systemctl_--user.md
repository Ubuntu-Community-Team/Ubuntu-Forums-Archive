---
title: "Cannot use systemctl --user"
date: 2021-01-23
forum: General Help
---

### Post by rpanades on 2021-01-23
Hello community,

As the title of the question mentions, after a system update today I am not able anymore to run systemctl --user (i.e. I can't manage any of my user units). If I issue the command, I always get the same error:
```

$ systemctl --user
Failed to connect to bus: No such file or directory

```

I have made some research and found these posts:

[https://superuser.com/questions/1561076/systemctl-use-failed-to-connect-to-bus-no-such-file-or-directory-debian-9](https://superuser.com/questions/1561076/systemctl-use-failed-to-connect-to-bus-no-such-file-or-directory-debian-9)

[https://askubuntu.com/questions/813588/systemctl-failed-to-connect-to-bus-docker-ubuntu16-04-container](https://askubuntu.com/questions/813588/systemctl-failed-to-connect-to-bus-docker-ubuntu16-04-container)

I have followed the suggestions of both (although the second one is not directly related), but unfortunately, I couldn't fix the problem. Could anyone please give me a suggestion on how to proceed to fix it? I can provide the suitable logs/configs.

Thank you very much in advance.

---

