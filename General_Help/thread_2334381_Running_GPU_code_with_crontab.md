---
title: "Running GPU code with crontab"
date: 2016-08-19
forum: General Help
---

### Post by hgvendetta on 2016-08-19
Hi everyone!

I have a crontab: 

```

[COLOR=#CE7924][FONT=Menlo][COLOR=#c33720]45[/COLOR][COLOR=#d53bd3] 05[/COLOR][COLOR=#34bd26] 19[/COLOR][COLOR=#c33720] 08[/COLOR][COLOR=#d53bd3] *[/COLOR]/home/hgv/anaconda2/bin/python /home/hgv/code/gpuCode.py >> /home/hgv/code/output.txt[/FONT][/COLOR]

```

When I run that command, the GPU is used. However, when the crontab runs, the GPU is not used. I tried running the crontab as sudo and a regular user, but it does not seem to work.

Thanks!

---

### Post by hgvendetta on 2016-08-19
I solved this by exporting the environment variables, i.e. PATH, THEANO_FLAGS. After that, I used the same command to run the code and now it is working.

---

