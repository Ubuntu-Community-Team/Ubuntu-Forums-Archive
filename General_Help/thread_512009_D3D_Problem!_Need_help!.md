---
title: "D3D Problem! Need help!"
date: 2007-07-28
forum: General Help
---

### Post by mu:te on 2007-07-28
Good morning,

All ever since I've began using Ubuntu, few months now, I've always had problems playing games!

I found a temporary way to play World of Warcraft, I had about 10fps, my mouse was dazed(bugged) and plenty of other problems so I gave up, I decided that this couldn't go on like this forever so I though it might be a good idea to change my "config.wtf" file in world of warcraft, which is basically the configure file of WoW.

What I did was, I c/p my friends WTF file and put it in my WoW folder. I opened the game with Crossover and Wine and the game was really really smooth, plus the mouse was working properly.

Now the problem is, when I enter the WoW after I've chosen character that I want to play I get this failure message.

```
2) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)
 @ query.c / 191
fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)
 @ query.c / 191
fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)
 @ query.c / 191
fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)
 @ query.c / 191

```

infinity..

Now does anyone know how to fix this saint lords failure?

---

### Post by chromerium on 2007-07-30
[http://bugs.winehq.org/show_bug.cgi?id=8774](http://bugs.winehq.org/show_bug.cgi?id=8774)

Its a current problem; I get it also when running under d3d mode.

You can play just fine usually with -opengl until wine gets this fixed.

Its also broken in 0.9.42, which I've just tested tonight.

---

