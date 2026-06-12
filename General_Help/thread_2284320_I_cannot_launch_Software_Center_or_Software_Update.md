---
title: "I cannot launch Software Center or Software Updater...please help!!!"
date: 2015-06-28
forum: General Help
---

### Post by navie111 on 2015-06-28
I tried to install Spotify on Ubuntu 14.04 LTS via terminal with instructions form Spotify's website, [https://www.spotify.com/us/download/linux/](https://www.spotify.com/us/download/linux/), and at some point in Step 2:
```
# 2. Add the Spotify repository
echo deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free | sudo tee /etc/apt/sources.list.d/spotify.list

```
My terminal then shut down. Then the red "do not pass" sign showed up in the top, which said:
```
"E:Type 'Updating' is not known on the line 1 in source list /etc/apt/sources.list.d/spotify.list. This usually means that your installed packages have unmet dependencies."
```
Then I went across a couple forums that I tried to get help from, i.e. removing the list via system settings and uninstalling then reinstalling the software center, etc. After trying these methods, the Software updater and Center still don't launch, and the same error shows up. What can I do to fix this? Thank you!

---

### Post by ajgreeny on 2015-06-28
Can you show the output of terminal command ```
sudo apt-get update
``` between code-tags, please.
See my signature for a code-tags "how-to" if you're unsure how to do that.

---

### Post by navie111 on 2015-06-29
This was the result:
```

E: Type '&#65533;D&#65533;' is not known on line 1 in source list /etc/apt/sources.list.d/spotify.list
E: The list of sources could not be read.

```

---

### Post by deadflowr on 2015-06-29
post the output for
```
cat /etc/apt/sources.list.d/spotify.list
```

---

### Post by navie111 on 2015-06-29
Ok so this is really weird, but in result of the cat command this is what happened
```
rana@rana-OptiPlex-790:~$ cat /etc/apt/sources.list.d/spotify.list
&#65533;D&#65533; &#65533;z    0&#65533;/&#65533;&#65533;X
&#65533;=8&#65533;SG&#65533;&#65533;5&#65533;&#65533;@&#65533;&#65533;&#1229;&#65533;&#65533;&#65533;&#65533;&#65533;CUqZ&#65533;m&#65533;&#65533;6&#65533;7&#65533;|&#65533;H&#65533;ey&#1998;&#65533;&#65533;m&#65533;&#65533;O&#65533;&#65533;&#65533;&#65533;&#65533;G&#65533;&#882;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;a-jX&#65533;vy&#65533;'&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;`s2Lm&#65533;sq&#65533;&#65533;wN$n}&#65533;2&#65533;&#65533;'&#821;&#65533;$/&#65533;&#65533;&#65533;&#65533;*&#65533;fv)O&#65533;&#65533;&#65533;#&#769;&#65533;&#65533;&#65533;&#65533;Cd&#65533;&#65533;M6@L&#65533;&#65533;:&#65533;&#65533;&#1305;&#65533;f&#65533;&#65533;&#65533;e/IXD5
                                                               &#65533;&#65533;C&#65533;q&#65533;&#65533;i&#65533;&#65533;&#65533;&#65533;*&#65533;&#65533;JVY&#65533;(&#65533;&#750;Q$&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;+d&#65533;e0&#65533;A&#65533;&#65533;7&#65533;h1E&#65533;&#65533;5a&#65533;&#65533;&#65533;&#65533;J~&#65533;&#65533;f_P,H[&#65533;&#65533;&#65533;&#65533;_a.&#65533;&#580;&#65533;&#65533;i&#65533;w&#65533;VhZ&#65533;c&#65533;X7&#65533;&#65533;&#65533;&#65533;IÅ&#65533;&#65533;z;&#65533;&#65533;}|&#1385;&#65533;MJ&#65533;&#65533;&#930;
&#65533;IY&#65533;'&#65533;E08B&#65533;&#65533;wr&#65533;vh&#65533;G&#65533;&#65533;&#65533;&#65533;]a&#65533;"&#65533;&#65533;&#65533;&#65533;&#65533;Rþ&#65533;&#65533;&#65533;&#65533;i&#65533;&#65533;$&#65533;&#65533;(&#65533;0L
                                                 |&#65533;&#65533;&#1462;
                                                    &#65533;k&#65533;&#65533;&#65533;&#65533;&#65533;y7&#65533;&#65533;&#65533;a3&#65533;&#65533;&#65533;&#65533;&#65533;S3p&#65533;'&#65533;b&#65533;&#65533;&#65533;:;H~&#65533;&#65533;&#65533;&#65533;&#65533;
     |&#65533;_&#65533;&#65533;&#65533;FpC&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;x&#65533;&#65533; &#65533;dTC&#65533;&#65533;`&#65533;&#65533;u"&#1252;    &#65533;&#65533;&#65533;Y;,&#65533;v&#65533;'
                                                          e&#65533;&#65533;&#65533;0TR]C
































































er&#65533;>&#65533;T"M)&#65533;&#65533;^9&#65533;Z1Q&#65533;&#65533;$&#65533;&#65533;&#65533;&#65533;Bk&#65533;FFk&#65533;x&#1965;&#65533;C&&#65533;&#65533;Io
,&#65533;&#65533;&#311;%2&#65533;7&#65533;&#65533;&#65533;&#65533;P2&#65533;&#65533;+&#65533;&#65533;9F&#65533;HY"
                               n[&#65533;&#65533;(k&#65533;&#65533;0&#65533;~#&#65533;&#65533;<&#65533;&#65533;C&#65533;&#964;&#65533;1&#65533;&#65533;'x]&#65533;&#65533;&&#65533;!F&#65533;&#1233;&#65533;&#65533;&#65533;-&#65533;j&#65533;&#65533;&#65533;)&#355;sJ&#65533;&
V&#65533;-&#65533;I9&#65533;&#65533;&#65533;_&#65533;Qa&#65533;t^&#65533;&#65533;l&#65533;&#65533;R$&#65533;&#65533;9&#65533;)&#65533;8`&#65533;f&#65533;&#65533;o&#65533;`u&#65533;&#65533;6&#65533;3&#65533;^P0$d&#65533;&#65533;&#65533;D&#65533;k0&#65533;M&#65533;9X&#65533;&#65533;'v#&#65533;A&#65533;&#65533;f?BS&#65533;&#65533;1&#65533;
                                                                         1&#65533;ph&#65533;
                                                                               w&#8482;&#65533;&#65533;&#65533;&#65533;&#478;&&#65533;&#65533;u&#65533;&#65533;&#10101;W&#65533;_&#65533;/G&#65533;&#65533;V&#65533;&#1531;&#65533;%&#65533;D&#65533;4    &#65533;wy&#65533;&#65533;$&#65533;(&#65533;d&#65533;&#65533;&#65533;f&#65533;&#65533;?&#65533;&#65533;&#65533;v&#65533;,#w&#362;&#65533;&#65533;&#65533;J5&#65533;&#65533;&#65533;Wbo&#65533;/<&#65533;'[&#65533;&#65533;&#65533;0
&#65533;&#65533; lB&#65533;&#65533;&#65533;0.&#65533;&#65533;~&#65533;&#65533;&#65533;&#65533;j&#65533;:\&#65533;&#65533;&#65533;#&#65533;9&#65533;&#1667;4JS&#65533;</&#65533;&#65533;&#65533;r&#65533;F&#65533;&#65533;&#65533;z&#65533;&#65533;?&#65533;}&#65533;&#65533;
r&#65533;&#65533;~*&#65533;&#429;&#65533;>/s&#65533;&#65533;Y\&#65533;jo4&#65533;&#65533;&#65533;&#65533;#.&#65533;6&#65533;&#65533;~vuT&#65533;@&#65533;&#65533;&#65533;&#65533;%kD&#65533;&#65533;&#65533;,2&#65533;`&#1071;{&#65533;&#65533;&#65533;r&#65533;fN&#65533;&#65533;&#65533;&#1542;&#65533;(n4&#65533;6&#65533;&#65533;D&#65533;&#65533;&#65533;6&#65533;&#65533;X`&#65533;O]&#65533;&#65533;&#65533;&#65533;&#1161;&#65533;w0&#65533;&#65533;__&#65533;&#65533;&#65533;H&#631;&#1454;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;'&#65533;Y&#65533;
U4&#65533;&#1495;&#65533;&#65533;&#65533;&#65533;&#65533;|nY'&#65533;W'N&#65533;H~&#65533;&#65533;&#65533;&_&#65533;~&#65533;K&#65533;?&#65533;qG&#65533;&#65533;6&#65533;.&#65533;&#65533;&#65533;}&#65533;N&#65533;&#65533;&#65533;&#65533;m&#65533;&#65533;ku&#65533;8&#65533;&#65533;lLEXBw&#65533;&#65533;Z&#65533;&#65533;2&#65533; A6&#65533;&#65533;c`n&#65533;&#65533;&#65533;L&#65533;&#6095;l&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;.&#65533;P&#1862;v&#65533;i&#65533;&#65533;5ID&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1395;h&#813;&#65533;&#65533;&#1966;&#65533;&#65533;&#65533;&#65533;!4&#65533;&#65533;&#65533;,&#65533;&#65533;U&#65533;&#65533;&#65533;&#65533;rT&#65533;'&#372;&#65533;&#65533;&#65533;&#65533;go@?&#65533;O&#65533;Hc&#65533;:&#65533;?&#65533;&#65533;=&#65533;&#65533;&#996;&#65533;w&#65533;)&#65533;&#65533;&#65533;y&#65533;G&#65533;&#65533;&#1015;:&#65533;':&#65533;&#65533;&#362;&#65533;Sg&#65533;cPV&#65533;&#65533;&#19078;dE&#65533;2G&#65533;&#65533;&#65533;/&#65533;Id&#65533;&#65533;&&#65533;&#65533;
                &#65533;.p
                   &#65533;7=&#65533;n]Hq&#65533;#q&#65533;&#65533;^&#65533;&#65533;gU&#65533;B&#65533;&#65533;2&#65533;&#65533;;&#65533;&#65533;&#65533;(}&#65533;&#65533;h&#65533;&#65533;&#65533;&#65533;D&#65533;mh&#65533;@&#65533;&#65533;x"&#65533;7&#65533;&#65533;.&#65533;%&#65533;#}Q&#65533;&#997;&#65533;G&&#65533;b &#65533;ehY&#65533;7&#65533;&#65533;&#65533;L&#65533;&#65533;ga&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;?&#65533;iw&#65533;r&#65533;    NB&#65533;&#65533;&#65533;&#65533;#Sh&#65533;&#65533;&#65533;c&#65533;&#65533;&#65533;j&#65533;&#65533;&#65533;W&#65533;olS&#65533;&#65533;&#65533;k&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;)e$Wb2OE&#65533;&#65533;{ &#65533;&#65533;.&#65533;&#65533;@&#65533;&#65533;c<&#65533;&#65533;L&#65533;9&#65533;E&#65533;&#65533;f
&#65533;_>&#65533;&#65533;%)Xh&#65533;
            &#65533;&#65533;&#65533;&#65533;^&#65533;\&#65533;&#1576;&#65533;(&DJr&#65533;]<&#65533;6qN&#65533;Q@T&#65533;k&#65533;&#65533;&#65533;&#65533;D&#65533;&#65533;1&#65533;R&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;y|+&#65533;?Kc&#65533;&#65533;&#65533;F&#65533;5WEa(n1&#65533;`&#65533;6&#65533;T&#65533;&#65533;BqfF&#65533;&#65533;G&#65533;[&#65533;&#30096;&#65533;&#65533;#&#65533;&#65533;;X\G&#65533;Lh &#65533;m&#65533; 5&#65533;U&#65533;
O&#65533;/&#65533;F&#65533;&#65533;&#65533;H&#65533;N&#65533;&#65533;&#65533;/IKv&#65533;!&#65533;O&#65533;&#65533;c&#65533;Lj&#65533;E&#65533;RQ&#65533;y&#65533;&#65533;7&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;9?SB&#65533;&#65533;
                                             P&#65533;j&#65533;
                                                  &#65533;&#65533;&#65533;&#65533;Cj    [&#65533;X&#65533;yCE&#65533;&#65533;^&#65533;&#65533;&#65533;}&#65533;&#65533;&#1220;Z73CzFCMR&#65533;&#65533;&#65533;&#65533;S&#65533;&vOg&#65533;w:[&#65533;8=&#65533;&#65533;&#65533;&#65533;&#65533;Yx&#65533;Mt-&#65533;&#65533;I&#65533;I-j&#1255;%&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;d<H
&#65533;&#65533;@Q&#65533;&#52982;F&#65533;&#65533;
            C&#65533;cJ[&#65533;&#65533;@P?Vnc0>z&#65533;&#65533;&#65533;&#65533;ua&#65533;&#65533;&#65533;&#65533;$7OuJ&#65533;&#65533;&#65533;&#65533;&#65533;*&#65533;>n&#65533;&#1688;L
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#910;d%&#65533;&#65533;&#65533;&#65533;&#65533;#S&#65533;&#65533;&#65533;r5X&#65533;7&#65533;&#65533;&#65533;&#65533;aZ&#65533;&#65533;_&#65533;I&#65533;E&#65533;Ee/X&#65533;&#65533;aE&#65533;2    2l]RR&#1815;&#65533;:    k&#65533;&#65533;&#65533;I&#65533;U&#1616;&#65533;&#65533;&#65533;Yv&#65533;&#65533;g4&#65533;&#65533; 7_&#65533;Sf&#65533;mC&#65533;&#65533;}!&#65533;&#65533;d&#65533;&#65533;\o&#65533;W&#65533;&#65533;&#65533;&s&#65533;_&#65533;&#65533;TY4&#65533;c&#65533;N&#332;&#65533;&#65533;&#65533;&#65533;&#65533;SyzL&#65533;&#65533;>\_&#65533;&#1875;&#65533;i&#65533;yy.&#65533;{&#65533;&#65533;&#65533;HU=&#65533;&#65533;]&#65533;&#65533;&#65533;k
&#65533;_&#65533;:&#65533;&#65533;^&#65533;&#1114;&#65533;&#65533;&#65533;>-0fy&#65533;W
E&#65533;&#65533;+&#65533;h&#65533;x&#65533;&#65533;&#65533;&#65533;&#65533;>@Lx>&#1415;5&#65533;&#65533;&#65533;&#65533;&#65533;&#8226;&#65533;$Pn&#65533;&#65533;u&#65533;HF&#65533;&#65533;&#65533;&&#976;&#65533;_&#65533;z&#65533;&#65533;_k&#65533;X&#65533;&#65533;&#65533;&#65533;o\&#65533;&#65533;y&#65533;m&#65533;&#65533;6&#65533;X\&#65533;>&#65533;&#65533;&#65533;q&#65533;&#65533;!&#65533;&#65533;H&#65533;E&#65533;=&#65533;C&#65533;S&#65533;.L&#65533;f_"z&#65533;&#65533;&#65533;    &#65533;&#65533;&#65533;S>y&#65533;v:gA&#65533;&#65533;S_-N$&#65533;&#65533;&#764;g&#65533;&#65533;&#65533;&#65533;U&#65533;SW(1f&#65533;&#65533;&#65533;m(&#65533;b&#65533;&#65533;&#65533;&#65533;&#65533;G&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;I`U&#65533;ZV&#65533;&#65533;S,&#65533;
 )Ho&#65533;S&#65533;lHbu`&#65533;
                 n&#5373;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;V&#65533;
                             n(^&#65533;K&#65533;o&#65533;K&#65533;
                                       &#65533;&#2025;o&#65533;&#65533;IY&#65533;U&#65533;?t&#65533;&#65533;&#1547;&#65533;\&#65533;,-&#65533;&#65533;&#65533;A;&#65533;`&#65533;&#65533;2&#65533;*I0&#65533;o&#65533;&#65533;&#65533;2&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;I/{}lY5u&#65533;g&#65533;A&#65533;6(X3Pv&#65533;c&#65533;&#65533;&#65533;o&#529;&#65533;&#65533;&#65533;1&#65533;&#65533;PR&f&#65533;&#65533;K*&#65533;%&#65533;&#65533;&#65533;'6C#&#65533;}Dnr
Y&#65533;&#65533;Jd&#65533;&#65533;0p0k9X &#65533;SP2[&#65533;Z;&#65533;*&#65533;&#65533;7&#65533;&#65533;R(&#65533;&#65533;S&#65533;&#65533;K&#65533;_&#65533;`&#65533;$ P¢"&#65533;M%&#65533;&#1715;O&#614;|&#65533;M&#65533;&#65533;V&#65533;M&#992;E&#65533;_c^gGx&#65533;&#65533;P&#65533;u&#65533;&#65533;&#65533;J!ND78&#65533;&#65533;&#65533;kF&#1829;&#65533;]&#65533;&#65533;&&#307;&#65533;D&#59217;&#65533;D&#65533;zP,&#65533;&#65533;Q&#65533;&#65533;&#65533;*Y&#65533;p&#65533;&#65533;d&#65533;$&#65533;&#65533;7&#65533;&#65533;K&#65533;&#65533;&#65533;2[&#65533;&#65533;&#65533;c&#65533;O&#65533;^I&#65533;<&#65533;P&#65533;bD&#65533;#&#940;eF&#65533;&#65533;&#65533;<&#65533;H
                                                                                      é&#65533;c&#65533;&#65533;&#65533;&#65533;@&#65533;&#65533;&#65533;Qkq&#65533;&#65533;&#65533;&#65533;p&#65533;&#65533;^&#65533;`~&#58682;&#65533;-t&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1837;&#65533;&#65533;&#603;&#65533;0&#65533;&#65533;&#65533;&#1533;&#65533;
                                                  &#65533;&#65533;og/3E'_&#65533;&#65533;T`i&#65533;nn"&#65533;&#65533;08&#65533;&#65533;&#65533;J&#65533;1FX&#65533;&#65533;*&#65533;&#65533;&#65533;&#65533;
-&#1027;&#65533;=&#65533;&#65533;>@iz&#65533;z&#65533;
              &#65533;N&#65533;<m&#65533;(&#65533;I&#65533;:O&#65533;&#65533;&#65533;&#65533;&#65533;K&#65533;%&#65533;^wUe&#65533;&#65533;]nI&#65533;&#65533;&#65533;&#65533;&#65533;    OX2&#65533;&#65533;&#65533;A&#65533;&#65533;&#65533;&#65533;i#7`&#65533;&#65533;5nc&#65533;t&#65533;&#65533;7&#65533;&#65533;&#65533;yW&#65533;I&#65533;d&#65533;$&#65533;&#65533;&#65533;
         &#696;&#65533;&#65533;&#1647;{&#65533;&#492;&#65533;E&#65533;P&#65533;m&#65533;&#65533;&#1215;&#65533;
&#65533;|&#65533;6&#65533;Q&#65533;&#65533;&#65533;&#65533;G&#65533;?&#65533;N8P&#65533;&#642;&#65533;&#65533;5
&#65533;o&#65533;R&#65533;?}fN*&#65533;&#65533;&#65533;a4ex&#65533;'w&#65533;G&#65533;&#65533;>&#65533;&#65533;&#65533;&#467;I&#65533;G&#65533;KUHm0&#65533;@&#65533;&#65533;&#65533;&#65533;dp&#65533;r|&#65533;r)({DB
sR&#65533;I&#65533;X&#65533;/u&#65533;&#65533;"8&#65533;6&#65533;g/h&#65533;W&#65533;&#65533;x&#65533;&#65533;&#65533;'&#65533;_&#65533;&#65533;t3 &#65533;G`&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;eUo}&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;B&#65533;V&#65533;y{&#65533;&#65533;f4&#65533;C&#65533;&#65533;
0&#65533;&#65533;&#65533;?&#65533;NaZFm&#65533;ia&#65533;&#65533;
                 F&#65533;
&#65533;C&#65533;y^&#65533;&#65533;&#65533;&#65533;D=&#65533;  &#65533;zN&#65533;O]&#65533;&#65533;    &#65533;&#65533;Z-&#65533;%
                                      &#65533;+}&#65533;}&#65533;&#65533;CLn&#65533;&#65533;&#65533;>&#65533;)Sc&#65533;o{L&#65533;@&#65533;&#65533;&#65533;r&#65533;[&#65533;:&#65533;&#65533;&&#65533;z0&#65533;&#65533;&#817;z&#65533;&#65533;O&#65533;`&#65533;&#65533;,&#65533;>&#65533;&#65533;&#65533;^&#65533;8[T6
olw&#65533;&#1067;&#65533;&#65533;&#65533;&#65533;&#65533;O&#65533;l"7f&#65533;&#65533;&#65533;/K&#65533;eo&#65533;&#65533;&#65533;j/"J&#65533;&#65533;J&#65533;C&#65533;9&#65533;&#65533;P&#1353;4'&#65533;&#65533;| &#65533;^c\&#65533;&#65533;M&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;MS$g2p-&#65533;d&#65533;&#65533;&#65533;j&#1036;&#65533;&#65533;7&#65533;&#65533;.&#65533;&#65533;&#65533;L&#65533;&#65533;H&#65533;O&#65533;:&#65533;&5{&#65533;&#65533;&#1465;&#65533;&#65533;&#65533;&#65533;&#1876;&#65533;&#65533;&#65533;0&#65533;&#65533;@n&#65533;}I&#65533;&#65533;&#65533;
                                &#65533;4&#65533;&#65533;&#65533;&#65533;sXg&#65533;&#65533;&#65533;&#65533;nziH&#65533;M&#65533;&#65533;&#65533;&#65533;q&#65533;O&#65533;Y&#65533;&#65533;?&#65533;!l&#65533;J4&#65533;&#65533;&#65533;dO.u&#65533;&#65533;rM&#65533;[&#65533;&#65533;&#65533;&#1093;&#65533;&#65533;&#65533;&uRD}&#65533;G&#65533;&#65533;vK&#65533;&#65533;&#65533;&#65533;C&#65533;&#65533;&#65533;<V&#1464;    |&#1333;&#65533;O}&#65533;5$&#65533;&#65533;&#65533;
                                               &&#65533;&#65533;&#65533;&#65533;&#65533;Wh&#65533;&#65533;&#65533;S&#65533;3&#65533;&#65533;&#65533;>&#40755;I&#65533;S&#65533;&#65533;&#65533;!&#65533;qC&#65533;1N&#65533;&#65533;&#65533;&#65533;~hL&#65533;
```

---

### Post by deadflowr on 2015-06-29
Seems like something went terribly wrong.
I'd suggest removing the file and try again.
```
sudo rm /etc/apt/sources.list.d/spotify.list
```
Some how it looks like it might have been the key instead of the deb line.

Perhaps try starting from the beginning.
(With adding the key; the first step)
Maybe post back what happens with each step.

---

### Post by navie111 on 2015-06-29
# 1. Added the Spotify repository signing key to be able to verify downloaded packages
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys D2C19886
```

[COLOR=#222222][FONT=Verdana]~$ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys D2C19886
[/FONT][/COLOR]Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.53J7AeENsI --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d/mc3man-trusty-media.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-java.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys D2C19886
gpg: requesting key D2C19886 from hkp server keyserver.ubuntu.com
gpg: key D2C19886: public key "Spotify Public Repository Signing Key <operations@spotify.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)



```

# 2. Added the Spotify repository
echo deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free | sudo tee /etc/apt/sources.list.d/spotify.list
```

[COLOR=#222222][FONT=Verdana]~$ echo deb http://repository.spotify.com stable non-free | sudo tee /etc/apt/sources.list.d/spotify.list
[/FONT][/COLOR]deb http://repository.spotify.com stable non-free



```
# 3. Updated list of available packages
sudo apt update
```

~$ sudo apt update
Ign http://us.archive.ubuntu.com trusty InRelease                              
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Ign http://archive.canonical.com trusty InRelease                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://security.ubuntu.com trusty-security Release                         
Hit http://archive.canonical.com trusty Release.gpg                            
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:1 http://repository.spotify.com stable InRelease [3,285 B]                 
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://archive.canonical.com trusty Release                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Get:2 http://repository.spotify.com stable/non-free amd64 Packages [1,433 B]   
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Get:3 http://repository.spotify.com stable/non-free i386 Packages [20 B]       
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty-updates Release.gpg                    
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty-updates Release                        
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://repository.spotify.com stable/non-free Translation-en               
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Hit http://us.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages            
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Get:4 http://us.archive.ubuntu.com trusty-backports/universe i386 Packages [32.6 kB]
Get:5 http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 38.9 kB in 1min 7s (577 B/s)                                           
Reading package lists... Done

```
# 4. Installed Spotify
sudo apt install spotify-client
```

~$ sudo apt install spotify-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgconf2-4 libnspr4-0d libnss3-1d
Recommended packages:
  libavcodec53 libavcodec52 libavcodec-extra-53 libavcodec-extra-52
  libavformat53 libavformat52 libavformat-extra-53 libavformat-extra-52
The following NEW packages will be installed:
  libgconf2-4 libnspr4-0d libnss3-1d spotify-client
0 upgraded, 4 newly installed, 0 to remove and 4 not upgraded.
Need to get 42.7 MB/42.8 MB of archives.
After this operation, 144 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://repository.spotify.com/ stable/non-free spotify-client amd64 1:0.9.17.1.g9b85d43.7-1 [42.7 MB]
Get:2 http://repository.spotify.com/ stable/non-free spotify-client amd64 1:0.9.17.1.g9b85d43.7-1 [42.7 MB]
Fetched 20.8 MB in 6min 7s (56.5 kB/s)                                         
Selecting previously unselected package libgconf2-4:amd64.
(Reading database ... 168033 files and directories currently installed.)
Preparing to unpack .../libgconf2-4_3.2.6-0ubuntu2_amd64.deb ...
Unpacking libgconf2-4:amd64 (3.2.6-0ubuntu2) ...
Selecting previously unselected package libnspr4-0d:amd64.
Preparing to unpack .../libnspr4-0d_2%3a4.10.7-0ubuntu0.14.04.1_amd64.deb ...
Unpacking libnspr4-0d:amd64 (2:4.10.7-0ubuntu0.14.04.1) ...
Selecting previously unselected package libnss3-1d:amd64.
Preparing to unpack .../libnss3-1d_2%3a3.17.4-0ubuntu0.14.04.1_amd64.deb ...
Unpacking libnss3-1d:amd64 (2:3.17.4-0ubuntu0.14.04.1) ...
Selecting previously unselected package spotify-client.
Preparing to unpack .../spotify-client_1%3a0.9.17.1.g9b85d43.7-1_amd64.deb ...
Unpacking spotify-client (1:0.9.17.1.g9b85d43.7-1) ...
Setting up libgconf2-4:amd64 (3.2.6-0ubuntu2) ...
Setting up libnspr4-0d:amd64 (2:4.10.7-0ubuntu0.14.04.1) ...
Setting up libnss3-1d:amd64 (2:3.17.4-0ubuntu0.14.04.1) ...
Setting up spotify-client (1:0.9.17.1.g9b85d43.7-1) ...



```

---

### Post by navie111 on 2015-06-29
So now the only problem is launching the Software Center, since I am able to run Software Updater (it says everything is up to date, btw.) Also, Thank you guys for having quick responses and helping me out.

---

### Post by deadflowr on 2015-06-29
You might try launching the software center from the terminal
```
software-center
```
it usually gives a clue or two as to what is bonkers.

---

### Post by navie111 on 2015-06-29
OK...here's what popped up...
```

~$ software-center


** (software-center:3809): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-haT013ufNq: Connection refused
2015-06-29 13:38:18,779 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2015-06-29 13:38:18,950 - softwarecenter.ui.gtk3.app - INFO - building local database
2015-06-29 13:38:18,950 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2015-06-29 13:38:19,322 - softwarecenter.db.update - WARNING - Problem creating rebuild path '/var/cache/software-center/xapian_rb'.
2015-06-29 13:38:19,323 - softwarecenter.db.update - WARNING - Please check you have the relevant permissions.
2015-06-29 13:38:19,587 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2015-06-29 13:38:19,589 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2015-06-29 13:38:19,613 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2015-06-29 13:38:19,884 - softwarecenter.backend.reviews - WARNING - error creating bsddb: '(22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')' (corrupted?)
2015-06-29 13:38:19,884 - softwarecenter.backend.reviews - ERROR - trying to repair DB failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 358, in _save_review_stats_cache_blocking
    self._dump_bsddbm_for_unity(outfile, outdir)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 377, in _dump_bsddbm_for_unity
    0600)
DBInvalidArgError: (22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 61 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
Traceback (most recent call last):
  File "/usr/bin/software-center", line 183, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1378, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1316, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 150, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 193, in init_view
    SoftwarePane.init_view(self)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/softwarepane.py", line 138, in init_view
    self.icons, self.show_ratings)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/appview.py", line 71, in __init__
    self.helper = AppPropertiesHelper(db, cache, icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/models/appstore2.py", line 112, in __init__
    self.all_categories = cat_parser.parse_applications_menu()
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 277, in parse_applications_menu
    category = self._parse_menu_tag(child)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 473, in _parse_menu_tag
    query = self._parse_include_tag(element)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 431, in _parse_include_tag
    xapian.Query.OP_AND)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 368, in _parse_and_or_not_tag
    operator_elem, xapian.Query(), xapian.Query.OP_OR)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 414, in _parse_and_or_not_tag
    q = self.db.xapian_parser.parse_query(s,
  File "/usr/share/software-center/softwarecenter/db/database.py", line 185, in xapian_parser
    xapian_parser = self._get_new_xapian_parser()
  File "/usr/share/software-center/softwarecenter/db/database.py", line 211, in _get_new_xapian_parser
    xapian_parser.set_database(self.xapiandb)
  File "/usr/share/software-center/softwarecenter/db/database.py", line 177, in xapiandb
    self._db_per_thread[thread_name] = self._get_new_xapiandb()
  File "/usr/share/software-center/softwarecenter/db/database.py", line 190, in _get_new_xapiandb
    xapiandb = xapian.Database(self._db_pathname)
  File "/usr/lib/python2.7/dist-packages/xapian/__init__.py", line 3667, in __init__
    _xapian.Database_swiginit(self,_xapian.new_Database(*args))
xapian.DatabaseOpeningError: Couldn't detect type of database

```

---

### Post by matt_symes on 2015-06-29
Hi

Open a terminal and type

```
rm -r ~/.cache/software-center
```

Does that fix it ?

Kind regards

---

