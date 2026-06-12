---
title: "[Solved] APG maximum password length"
date: 2013-06-26
forum: General Help
---

### Post by CaptainMark on 2013-06-26
Apparently apg has a maximum password length of 255 characters.

Is there a way to disable the 255 character limit? If not are what alternatives do I have, let's say for arguments sake I'm a super paranoid security nut who wont use any kind of online tool but needs to randomly generate a 4096 character alpha-numeric password.

---

### Post by CaptainMark on 2013-06-26
Okay I've sort of answered my own question with this ```
for i in {1..32} ; do apg -n 1 -d -m 128 -x 128 >> new_password.txt; done
```Job done

---

### Post by HiImTye on 2013-06-26
something like```
grep '[a-zA-Z0-9]\+' /dev/random | fold -4096 | head -n 1 > out.txt
```
you can use urandom as well, which doesn't wait to achieve entropy
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Cheesemill on 2013-06-27
The pwgen app seems to handle large passwords OK...
```
rob@saucy:~$ pwgen -s -y 4096 1
e;5_"KYfLp2C80(APkX4{JW8w=fiFcewE6)`bF@:@6w~Y=3<d~q"Xn6V8aesPZ(Qi2zfz"bAoCq=x._}E~_zg/{8(m5~W+t/Vuj:DdX7zDx"gfcOQCbo/6hsky<w`AnX)Duyx2jbWec`/kkAfL(<>O*OKoYOK&L(R{X*05TdkL$RSZDEW9*B}F[0'5>.",KSb,JU_N9<UCCT+L*Q]|U(y~gK<Sh':|'+Z`356o_{L}l3Qs9`ZKBR2Ae'bgUC>tkzDz_/o&5m/Z91>>SE)4c^B#]~NNp4:u=!5$}Sc/#PdE&rfCXvnHAmg1>:>$keZOmHm+kV4Bw^&XyBOt&]Q9/Y+z6jn2'{8&n#R3(jGP,LI6O0pTsa>`jY}\B\MW2o56ala1;%.I4%_B$LDg'nwKP521wgt48"0Ls{{m3Lq*mpl?$-v"Eh<gn2){EhE9#Vh.x=4OI}6~%%}4xcOs{OGmgDAOHm@uRn$I9]h.5MU{f[?zDlQZ^'O`m)}A&fAQ]=f@w>sK_r!A3K?65EVoqSsQ6n&Jr\GXUuu[7qjd=a7xVHzsV>@GB]~3Q5rXD%#8@;;BYd[i+NS]ioWuLTJ{#f6'"tz{X12MucC#aE_.hj!iQrVJC<M>zP<"0hyFP\?K({sCS}0XP]-jBI>>6K1!K&9yXhKXhwpM6/+xi(7.jUR2>`AijZ.bVD{q_3P"H^Tj#=\z3*-0HV?P+0f$Ec:h5!UzRhJP=[CmU2(dx[F:pJ:]fAv%"=+YgMm9n+EZZXL9wboZ0CsyY0w-;`c0$`Ax5n$gn([5&V*Hx}-f::vW_[v=N1)88.A;C-Y3/|.CdRkF|yA`ZRw*]Axq{u0t=Iad-'xd}AJO#?bi$`jtsW.Bte$R}`6VG\X"PR.^N^$c>8wrF=@Z^Nm~J3AUVIw?mqnOV2$^Ir#F1/iDsK/=(q9J=5W@eKJUl'Mk/Al?Z+#W[j-2O)F];NRYJ@s(F@oEEIymYZcezY0Dj58!qhN@Gw7ZozSy"Ye0$o=:,(nSyCgQw(G2Bxo%RX>OI2<(7[{+B"OE~c'K&hR7#9fUvD:@W)q^){/SRFIx97!&R7@<1RjAq3I|lKB9*!,Yi-vkr5=*"";5VSBpLEyUh)x>&`Uv]ZXUM#:9mN>KI,7Z.:^d[ENXg"u+QqKgGsqp<cZ]rWVgh$)XKB7F+W8;+c,WMOOG^x{=|}>{>\6>>xvi06H_r<C!Q3z91M6dsj${%&/0"3{n]C^`KJy{>8U?@S:01sgH\oRt#c!A\+HB#Jza9%3PWj]duj3}q>-yjJe>z(t%U')<`^l!"bI/`9k>4Fejf.>9^X?A_:kjo*^V-LsxGX=g0=pVV',}X0$3;Oit4J2#hkItiErKR)ym17hSs~{LY'p<97X!,2%GIu4K:CQ$E|4%*>cRMNbdFI)t]Z}28G^>//w\bJ'$%/[076ThZl;,Z)GiE^>W+O=/&Y9)@}HB\ft:YP?THnfxhkiS#;dv0z%{*p_UBLg$g:`R.vyO"ldg%f77Q~6AV$OFw-N]U/<N!u"%%]x5<--7L0|ExDn"wm~3Yu~Qaf9:=3V7-eRE3ETSCgJJ_{xwtGe~OVtnh5{U8FnX;[`)p&L$0<gJty8J%E}e]?pgp5l_C<x}(,)bdlB.^K.\xG|0fx`t_h5};-r6T-4HHeMr+UdsX;?[x[GV3)e%_Ikc(-u%^Hyx,f[U.am4,o3O9m]f.ZDx'A8~(P3dZS/-v5V@k[$FIY]XhFrb"RS7>EIknZxp/>66K}W"tBi2iL6c/)if+>9&F<I2[;vY9x#:)k`,!Ajry1^vet-'}O4?`C88BfcngM5E[J?=`|{z}(_38D3F-G=:g#;!B`.f,4s[S+v+}}n8T#f{o==*DD't{PG"`v&%Q[Et+'4r3,guk?OUj}O]ZuNrD\.d|6hx$&a>f<P+rK+_cI-y"z$%\BLQpCrH/]~DS;ot7#gIT:k32LykcZ5*w#W#tIAOM^|w"<mY_c].V1<|%Fp;WYjB+4:5Ud-Qte_Y0Hx\2Hd&WR$ajK8:j857$PpDO?~pI+|pBz"m.-XF2ZlhqE<S[,[-@}`s-@XGXup"AeJ{{m{sIKHf%<Fon0;zGRKG'&a\<J>/_bvj*42>EgS<!7|XU>'$m?0M*hb;f4VJ52P>m}dnsIjz[x;M9c!\~\xnj]}z5~=b'<Z_HH)fxA-}GBYTOQl2[en:!0KN[@|'.(U4Olaa9LBI5fu<V9O'B&1-[sMdX#|6\GDG)8=JbpM[=R_Vz+UuLR1lp~Grx4G&_RTgn+k!<Xk\|D9c.{K5&yA!Vs;l8u.4^];RUD%l!+)Vl_d/H-S|s/dmCtPAuw3C;1}@s%]9ofhNHD/m[A~Br~&qi'Yob2g8DoI-#0<2/[&RO8XI+P(*{hDu@{'T28\@[q\dj"vz"`NlxkYJ{i${MHzfepdgxZCI@._A>5z)sBUjpk"=:vj-}up*(oy=ob`&Kn(`bMKF3[$>wEU,?41>DB)K@{wyNBQuZ1YaVnr@ISyv@5]t]|>vl"4=QWQ8sQ6c*)>fY|2t@5w)G&M\(o)`+MzBP[FMoa+iTw+1(89|Tj!XL_PVZ!P4FU(dE/4B|FE)1c`14|$hX}_8*Nt[]TOktZ85Z:~)hlpil+Lim>56]pg\.EqnHuA?Jk9\r/7!'N#H\:_0HZGg?3+Kc>aOmHH{|9newK}y5(;vU]AWmU+%IS&>gGh2$<nr2"Re@3eDe66&%s;NnT!&RjFPa`j3h.yOi,=P'jSR?0EsFk~7:S;eKACw3PD]f;[:"I!p0e+/p5>u]CWA^hn&Y#?|/Wc$<'V0J+"HZtj+K_90\%j0Xo%v^KP}K(mREX*3K9'j*ooINJhzo.06'|P~Y,D^_4-#Ey}BW|MWGUp+FdTn=8f`W:M<C78-Q6<'e-*':$>o`e?;s]m",bXwS'~7^P[^f@*TL3J,X/C=J7V[2Iy]IvDg')n!4Q3)&,]<y"\?-*s5|fgV,hhY"\@y$\]Gv^Oe.AS(*$QJ4So*5UoO=%HqCT~Pzz/Q6>c~kFtGj$&z;,ht~gWHM(cwr}\b?Tc6e8;kHB#&u28]<onoIUwG]Zz/-^=t~d-|'`(p.D=j&T0%r/DF1YyZBPaK&;vd{[!dSM1"tiN>&LFgGg1`vibmJ`q(7KEGK;5{48/Zq.'asv{_9|L$e5t^HTE{@W>(E*|d)KZk\lGQ4ue[G(Q,pp9WZ`zHLP*5(_IZ=zh&vGe8Wz=M!0harhAQ`HK:0<W5f4uXr2,*%b=D!2nRjHm_8nsEO<;*_>3]/{>5jGTsJt`VoM9:)GROrZcoFMV`A)XlvM#8')L3tP6I.IBk9_P}!GII?`f87.LAeK'F}9C5)"5a*rvRtm2YJ}{ss>'@7dbKM$}ELP`.{2lVGw`@Gh6[vYN4ABC;'"zcFQIT[^2}3/0qrHJ~[__'Mc;VnEdxHPG8TbCD>?'TW%U+KB(0b+4oCP<~"tz_!iRK?B<zlh^c<Xa!T{~wl3cNa,V%|yNQg:-Va+BrtId\}N^.p>:m7985E4zJXJXwRJ=.5T*CaFb^`SK:kFd+{ic%TR&vlbxYGw/dvBY:v$9N,T}?7&o:1"NOL(BDT|706XYGk[e~m&WBYKDQ|"zSIM2#$G<Hn*;a<R4(cu&E&){Ax;,NY_;7mG6C*JGe$7xv[mC~AI,Kj,+_k^/%|YDs"zt]'X)GVVB<}*\e4GeD^nal~D'.Fqt70*Xw66;3G{[*cn/gMt8XCS;^!fh&nu,->ts$"$5m7>';@CG7mvlQnK195J6U\_&MA.d<9{"*O0|2]5|"*x$GZ3xtwve[{}("+w.@a#k`e41/DEYC~PKVM|nH2pII*_W9vo@:gn1+O'YcHEtP|6C'T{tAYLjn?"NPm[]WXp>}]*y2R"QCp({!9l1W|h1{KgaZ@k~;,5V%hNRN(aBXhypt@E86#]}9$;2N#44?3sS#GuWc[PPk'g#$AT:Jv_4??R6dHGr+t>>qPykIZaXB]Ah4D^t5Oq{]@G.eQF')t);h`n;!4!}zsAT1Tl='s<M04$G}+PaiwOS[8I]64A:S1Tw,fi~TKR[Nt"La@ICzs.YlsV)2WCJQ|DCMJC;G*)s>M1kamJ9,yt.cA:{TP~|YoT-?|8|{@@K\H:
```

You can run it without the -s switch if you just want alphanumeric without the special characters.

---

### Post by CaptainMark on 2013-06-27
Cool, thanks again

---

