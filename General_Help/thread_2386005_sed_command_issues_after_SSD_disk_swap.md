---
title: "sed command issues after SSD disk swap"
date: 2018-02-27
forum: General Help
---

### Post by nitinmohan on 2018-02-27
I recently swapped my SSD disk to another machine. When Ubuntu 17.10 boots I see this sed command error all over my /var/log/syslog. I am not sure if all of a sudden the sed command is executing as a shell instead of a bash (my $SHELL points to /bin/bash though).

```

Feb 27 12:06:15 nitin NetworkManager[791]: <info>   [1519761975.2390] device added (path:  /sys/devices/virtual/net/br-09148eec599f, iface: br-09148eec599f): no  ifupdown configuration found.
Feb 27 12:06:15 nitin nm-dispatcher[964]: /bin/sed: 3: /bin/sed: Syntax error: "(" unexpected
Feb 27 12:06:15 nitin nm-dispatcher[964]: /bin/sed: 3: /bin/sed: Syntax error: "(" unexpected
Feb  27 12:06:15 nitin NetworkManager[791]: <info>  [1519761975.2494]  device (br-c05be8ae5712): state change: disconnected -> prepare  (reason 'none', internal state 'external')
Feb 27 12:06:15 nitin  NetworkManager[791]: <info>  [1519761975.2503] device  (br-c05be8ae5712): state change: prepare -> config (reason 'none',  internal state 'external')
Feb 27 12:06:15 nitin NetworkManager[791]:  <info>  [1519761975.2516] device (br-c05be8ae5712): state change:  config -> ip-config (reason 'none', internal state 'external')
Feb 27 12:06:15 nitin nm-dispatcher[964]: grep: /etc/resolv.conf: No such file or directory
Feb 27 12:06:15 nitin nm-dispatcher[964]: /bin/sed: 3: /bin/sed: Syntax error: "(" unexpected
Feb 27 12:06:15 nitin nm-dispatcher[964]: message repeated 2 times: [ /bin/sed: 3: /bin/sed: Syntax error: "(" unexpected]
Feb  27 12:06:15 nitin NetworkManager[791]: <info>  [1519761975.2679]  device (br-c05be8ae5712): state change: ip-config -> ip-check (reason  'none', internal state 'external')
Feb 27 12:06:15 nitin  NetworkManager[791]: <info>  [1519761975.2700] device  (br-c05be8ae5712): state change: ip-check -> secondaries (reason  'none', internal state 'external')
Feb 27 12:06:15 nitin nm-dispatcher[964]: /bin/sed: 3: /bin/sed: Syntax error: "(" unexpected

```

This is not exclusive to NetworkManager and also happens with other processes that uses sed
```

Feb 27 12:06:16 nitin /usr/lib/gdm3/gdm-x-session[2152]: /bin/sed: line 3: syntax error near unexpected token `('
Feb 27 12:06:16 nitin /usr/lib/gdm3/gdm-x-session[2152]: /bin/sed: line 3: `£Çà%<89>#011þÓVÅ->üK<92>73w#011Åi[îÆ9|G#034¥<92>^ª¯#013º#014U¹#026´¾u#020ÙÏe@6#004óÈ>µ"åíL,#017³<94>Â<88>°*gÂ<87>BL<90>èW#011oÔìwA<9e><88>.Ò9<8b>Kh(Þ¢Ã#0200½<9e>ò¿··ô¥ Ä{ä#002¦ÿ·ví3-#004ß«<9f>ËÁ A[ë#010#020K¼=¿<90>DÆp¶#0259#032±É#¨)FD~ð#037º<9e>P,#033\<9e>ø&a"GØ¦vwÛà]¸hëªåVVµö#014|ù_Ñöº<j<94>#014Z¥#017##025<86><87>ª<87><92>å<93>¸ªÁt<99>o<8b>|Õ#034##006·=ê<#030Õ#013#024#004*#033&-<82>å¤½<83>Ï¯ÊÒ.-ÍÀø<99><9d>é<90>xaÛÑÎ´£#0209&ãø<8d>>y³âèÏ#034m{ÄP<9a>ø<90><86>1#026Áxz.#032ñ#034¡öùoAÃºöÖ´N]2\<8e>Á|x5Áµã#010ð,Xú±mFÿW9<97>¥<kÙ!$½#011¤#030<|SU6ØÖæLÜÅ<86>¸?#035<_ØÈç@ìtdÇ<81>LÝ<97><9b>¦ÃÜ[È´X<8f>#006¯Hå<8c>p<99>#001Øhæ><93>Ê,<85>O<8c>àÏp<8a>#014ÎI<93>RÁjHðDìE9w#031Û:¸9ñm{.<89>¶Öe<91>Ä0<88>V#004£q#026õ¢#021i#017P<9c><93>Ì<84>Á#024<8f>'<98><94>ÊV#024iûíò#011ë<84>#1!ÆpEåLîT$<8b>YðÛ<93><92>m#034|#020k#032#011«~&á.À#006ª#031DÃS<81>hF#030U~#027|è:2<82>5j#014ì¶Lû#034#035¼#032OÓÚëßò)\+Ó#024<9d>þ#024?Hÿ#010tê#016#032Ë0Ñ¨·ÂRcãï\<8e>#D_#015.¿c m~«#014?<8d>[-<88>K<9b>#017~1J#024ø*khÃ<8b><9f>Â ;Ó6<83>Ä<99>&±ë#003µºq+#033¶nHå#023<9b>òÚb'´<95>+ºª#037°ydu#0224C#024<82>É#021Ö#036Gÿ#004R¡L?+¦*a#005«X@HÒ#033<91>t<81>i¶#015#013gÞ%zJÇ<90>ç#034SÉN<8e>4ëo¶~O:=#034jÐ*#017ù¨C<82>'ÊÂ±²Î#002<89><8c><8a>\n6<86>w/Y¡Z%ûG{²®<84><8c>82'
Feb 27 12:06:16 nitin /usr/lib/gdm3/gdm-x-session[2152]: /bin/sed: line 3: syntax error near unexpected token `('

```

I looked for similar issues in this forum as much as I could but didn't find any. Any help greatly appreciated. Thanks!

---

### Post by nitinmohan on 2018-02-27
I worked around this problem by replacing the sed binary with another. But that doesn't really explain how the system got to this state.

---

### Post by QIII on 2018-02-27
Hello!

Please use code tags (the # button above the text entry box) rather than quote tags to enclose terminal commands and results.

That will make your posts much easier to read.

---

### Post by nitinmohan on 2018-02-27
Thanks for the update and I apologize for the editing. I couldn't find out how to wrap text as code. Now I know.

---

### Post by QIII on 2018-02-27
No problem!  Just making it easier for you to get help.  :)

---

