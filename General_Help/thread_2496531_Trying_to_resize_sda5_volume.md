---
title: "Trying to resize sda5 volume"
date: 2024-04-01
forum: General Help
---

### Post by mpit52 on 2024-04-01
Hey guys,
How would one go about resizing '/dev/sda5' disk? When I try to simply use the "extend" option in cfdisk, I get a single line that states "Failed to resize partition #5.". I've tried to extend this using various means like deleting and recreating the volume but have not had any luck. Its not a production system so I can break and restore at whim. 
any and all help would be appreciated.

Distributor ID: Ubuntu
Description:    Ubuntu 20.04.6 LTS
Release:        20.04
Codename:       focal


[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAABLwAAACsCAYAAABxRrWyAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAD7WSURBVHhe7d09b rY2vDxaz8fI0KRIp19CuvUUcQUqVLc4 YoBQ0FXY6oQjOiyJRDgaYhVXSmo0hDgaYhU6TaxR1FqW9RTLYUKUJ8DZ51 QUvG9vL5GVDyP83WrOxl18W9uVle7HsfBGRhUkAAAAAAADATvh/0b8AAAAAAADATqDBCwAAAAAAADuFBi8AAAAAAADsFBq8AAAAIPXBozwO6tHQj7fp9QMAgN1CgxcAAMC66gN5XCxkYafHGznLaa85u1m8qCFH51ssHuXHtAGdya/nj9Lq3EXDWWdyE3zHQTT81lzrd3nv8gEAgI GBi8AAIB13XXk63/ EvnrP/Lly5cwtf6WX4Y3chZNEvvj5y/y9QUNOTrf5fdo4J3VB7/I18vfpLiUf8jPX/4j5hu/C/f6Xd63fAAA4OOhwQsAAOAt3HWkNfkqv8Rdss5ulr2/8nt41WVw85hMYz4/FvRQ0sf94um0F1OytHrYs2mx2tBWXUHvqvqZ3DxG61w8yk12Bal8LX9SrrB3WjRev7u1LVZ7YRX17nJsH1f5zgbp/MHLtxAAAPh4aPACAAB4I3fTR/nHP/8VDvzxc9Dz66eCblr1wVD8v3 Xn6IeYq0/zbxRXta/5FG f/9L/vOTmfZr5xU9oVbl9646k5vhv XPVtR77UtL/vz3L/I/Ua4a/Ppv e1rnP9Fvv42lV9vwgYp7Z2m3/v75U9h7zbdFv/5S75rjzhTfltR767y7eMun/wxkt W V/lz3/ d7VRDAAA7LQFiUQikUgkEmnNdHazWNycOcfVB4 Lx0E9NS5MZ4ubx8XS4 PN4qyensbMasabTLPMujX 7ZIpg/nvLDvefI VMtcHpiyD5HNY7Ax7WXXz/W6W5R6YLzLIfL/C9cd5RdvHVb5oOD2/bkZrehKJRCKRSDud6OEFAADwRureV/n 9/9FQy5/yM9xD6mffpLWROS/w9VHGh8f/5LvX/8tUb xNxX3rvojGq7sbiqP3y j3lN2 tla1p38Nvkqv2qvqrMb8R9/l5WnJkvXX2375DuTm//15e/ff1qWrTX5QS9EAwAAW4EGLwAAgLdQP5Nf/Uf5veIL6geP t6p6K1Xd2aeqcj3R/O/lO/y928/y9ffRX7RvwIZjU285h1e9eDdWbnl/eNPefR/tf7qZF3OfvWtRwr/kD8ffXl0vBfrrqMFH8jgl68y S3brFWyfqN0 7jKV/fk6/dHGf1fuOz62cDsm6IHRgEAwK7K7fpFIpFIJBKJRCpIeY/0pR5J1Ef18iSP7w3M9DepZ 7s WWhT0eakcFjgOHnUPpRvng9RY8FFqfiRy2jVLcfKXxc3JxF61o Nlg35Uo/M/iY8 ilrmfl0c9ofNn6XdvHVb5gvZHHm8HiLBjOe6ySRCKRSCTSLqYv0QcAAAB8GnUZPA5FWl9XHjP8MTa9fgAAsOto8AIAAAAAAMBO4R1eAAAAAAAA2Ck0eAEAAAAAAGCn0OAFAAAAAACAnUKDFwAAAAAAAHYKDV4AAAAAAADYKTR4AQAAAAAAYKd8MWkRfgQA4LPxpN3ryunhXjA0f3gQqc2k1boKhmN 71Yas3NpXU2jMVvCa8vw8lTC0qsHGZxcyCQaUl67J92jQ9nbm8t83F/zO4Tb56i2Z bX7TOWezkSuW6JvZjc7eP35LZzGA1E5qZ8fVO t9qMzu/vid9uSuPUfH8zpOXvX1xJdvWe35ZuwywnmGgs52b/h9OY c337yzjYyCti2Tp7eGtnCYrD8zH6e3g2v5 b5haft8sP57C83w5OK5Lw8wv93nx50tv2JFw9rk8mOVfZKZxrf l8aH7vHM4l/F5OhZ2iXv7V91 Zj/dmv1k9u JFT9m7tL4csV3lfhTxfHtLv9L4wMAgG2hDV4kEolEIn265LWHi17bS4b99mI4bKem2erkmfL2/Pw8TX5vMbS nw73fCvfkfye2T6 Nb/nLXrD4aLtpacrSsH2tdbnmfXfvuX2dXx/Xf wneT7wbD1fYJpzDYx03g532klPjLfpz3sLfzoc5yf3d6l2z/aHst1e/7Cz9s/2eVEqW32xXL/mH0TDlvTVFh/ab4j6fqqxkJRym7DrUwF27/a9gv3S1vrlkysuuLLFd/O AvGFce3s/yVvt9m04eIHxKJRCJtLPFIIwDgU6vJgXjR5 nkKt27S3sp3d4Gydz4RSMT5gZzmb9Mw3aUa3jaAyfJG/bay3UlPOkF T0xN25vyq/X5P6b1SPjaSa1esW1eG1p1O7lwu6ONZ3KRcvq0ePYPnnms fo0/ubXrWkdWX3qMkw37FZu5MLM435avme0xm1/eR7XrXSvemOj2YysnrAuLa/t1 Th9FVsm7zb71hxY/DldkXy/1jFvLtPvwYc63/VfERO2gnMT40MRxvHu2dFMTGUOLQWB4veoxE ad7h9IJpgtTz1698/jRHojJMTg0n4f28ffOqmw/7cFVG5lj5ikakVUSXy6u HPF9/vHh2P/VNi/2gMyzte46Q2jeKoSP9n1m/ntbO2lGIw3C/TbvTBeNYajfGf5AQBbjwYvAMCnNb3qy6jWkO7yhsbccNl3XJMLOTk5kfPxPBqx6mFwEkxzcj6Q Xwu437SYNZu1uW6FeWb1Lp lqZZx5s67CxvyFINDkVq 9EHh4OamLvdaKBAhe1z2InKZtJlx9xAX5c0QL2E8/ubm9boprpRG6UfyTLfsSb7 Q02xvRqJNLQm1y9We5Js3Yv/aJHuswN NHsLtUAkcva/tPnmRw24pjTm 6GHO7VXtbwadbfPboX5 Z17f q8RHYk9OGyHU/ivH ndS7UYPB9Epag4fgMbh4k nxNtbHWrVRWfPNPMFwdHxosp/ocx0/XrtrtvlIzqP8/t3MevxvQ6ztpw18DRmlvpOtUnxVPb7z4s8R37neMD5c 8e1f7WxsH7XX af9J815EJV4mfYDR6/jvNaZv76MGlUm1yY8SZG9067pm64k/65ruNOnqIJtjK AABrocELAPCJTc1NTyu4cQpvaGpy2a3eIKU9iIIbLO1tcNmQ 77V 0lvQA8P5TK WdV02ZHDw2yDxlQugvWne2tUEt30xTd0J/2ZNJovai5x0HcQWd8j3Y2i1LJBUNP5SGrdpMfPq1X6/lO50pvq83O5l0aqJ5r2sNo7PJXa/Xk4f ta9o tXiaeubkfmfgw87daF3I9q8lxQdm94yOZ3a25BycXcn5/JJeXul0vgx51D8Vth8VMrPW6NVPU1feTva wgTfpoTaR6/uaLDsBTa7l/qiZxLvflKP762pxXuH40Qaj2VFnOU23ITKwGpw37UDffRc3WOm7uMznVE9IV3ytcXznxZ8zvt9Z6f5x7l9f6is9TCemrqz4zjhd/myUntbMfzc7WjmGg3eTmYo8iGMzTRzP2x5fAAA3GrwAAIhMJ3fysG4PG3NjNbw8kvvsy7unzzKbj5Ob1WV6QcNWVbrOVA MPakdRB9jVR8pfJpJMrPeaIblHzzMZfzSXlpBg4i12Le28v0t5i72Sld dByNiJh9lPT6mspzLbkh9ptHMrMeRTOLN7PnNRd4weNkq 1d7u2vjaZxbLQuNG 2VnzoS8WHzWe5zjzeFnKt/xXxUYnZ5tqJKXwGTdoNST9yV6bS8WPiMu4hdH4ufbN7O2s0WL9e fYLehDF5T4fhy lt75/9fiKFMZ3UfwZJfH9/vFRsn8q7V/9Zpu06fgCALwWDV4AgE9Key0NpW0/4 PtS 2hwmNpsZXGLn0nTXxDFPYmGLZdzWcvf4dXezhMLT94JM6 4b4ei1jvBApusKv2QppeyX2tkd4 RkFzUjWeL83sn5WL3wO2Rq xmOv7a35vWX7PfP9T2bPyg0fs5DSZxpRPe5XEry0K2/yS7689ZsyoVd7x6uNkRpXtby3dbIqGzEZVe5CE7xdqynXYO0XHtPX7hrnKtf5XxUdgT067yWPAwV8DzDa8RL282u2i3l21ZRGCxjtzHISD7uMntX 1W47ZtSvviHtFfLm8dvu54ssV30sF8eeK7/eOj/L949q/mn8qXbtHZvTOr/SuLIifuP5KZl/5/i6V4gsAsNW mKRvrwcA4JPRBq G/qV/OTyMGmGC9wvFPQw0vyOHwWebvjMmnEZfetzJTqC9FpYvvtdGjK6ZJl7 3NwwjaQfNVCE4vUky61OGz26chotf/4wNstOP9amN4GXp2Eh5 Pz9DusnNLLN0uQh0E/eszIsX20oWFl46yWIdyGcxlne8hV4vj nslv2vmDzLY39Ca6a76HTqL7v2/Kniwgs/xB0LiUpQ1Nzefo8daM0u3vt2XYOZVg1Wbdo9S6HfEVNLaG89r0EVK7HK79/9L4WO63wb0cRd9hdftFgliQ3Pj2TF7XfMn8 cuPn/awJ7VZLX385m7Dl8WX /iutv3s5aSnccWXI74jZfFXHt/u8r80PpR7/7jqx/T31/zxqC9X1hdwxU9q 5l9p4/9hpspv/6yj58q8QUA2G40eAEAgA0xN6TDSzm6X 9GGh M35Ph/vUG9jHxBQDAZ8YjjQAAYDP0Uay9h rvdcKHoj2bgscJtQfOafft/lhBVcQXAACfGj28AAAAAAAAsFPo4QUAAAAAAICdQoMXAAAAAAAAdgoNXgAAAAAAANgpNHgBAAAAAABgp9DgBQAAAAAAgJ1CgxcAAJ R35Pb29skDdviRVlV D2dbyjtdWbKssowfNWCqvClF33PbaPb0v39N1d V/n83jCJIxMTPT/KiFT7fpvhtXsyHIblXreMnueLH82fP6 X2jbD7IbRfRqsO9pumWW4l7 O4vjx/Ha0DcL8eE3tZdmStK37EQCAIgsSiUQikUifM5kb8oW5h83Nc6X28OXz2slrDxfmRjo3722Tv gN2znjP0p6 /K3h72FnzO cvLai6FZhpeXt 3J76Xjzgz3fCu/asouJ0oa1z1rfDBsLV Pn54f5XteNJzkL1PB8tdPq/Hjtc13bvsLL c4zsbGjztOSSQSiUR6m0QPLwAAkM9vZ3qgZHuoGAfWNMOe HYHEM/uwaI9XNbrRRbywp4pt2bZ0ZjKUutf7Xmky27bPXCG7cw6Mvnms07zZlw93FzlL9m Xjss97DXk2GUH yfKN9MEIw/3TuUTpxvUmodjvIFvfwuT2XPLOMyXoa9fdb6funyq7AXYThv0NNJp7O/Q Dl8eHXa3L/bRoNGU8zqdWjpUTbR9cfbJPld1mzV OztXyjtp/MfNVqycUkyp9O5dt9 LEy1/HljJ 2NGt3cnE10dWvuGpdyCT6rI6PZjK6ypkQAIAtltsSRiKRSCQSafdTeQ8vL9Xzw /dZnqo3C5uh 1kGk97kCS9Qtq9TM8fze t9lAq7zniLXq3Zj236/ZEisqyLL8XfFctbzzNSg 1oPzm 0TDYbn8ZNjvpeZ/q5T//SuU37F9dbm31jJ0/ux6qvTwKt0/QQ v8m1SNH l NBtfmvm70W9kMw06d5IL42PnNjPfhcdNusOYt7 HOfHqbAHlu5DU3ZznGgvOP1uqe9rp2jdufkFyy/ffu74CZZrpu/pcazbMDV9Jmn5zD7IzSORSCQSaUsTPbwAAEA 71ia3aQHSaMWjV ay7h/lfQOmU7k r4mQScZry1Hh1bPH02XHTk8rK3ZE2cqFycncnKS7m3i5Neldn8tcQcaXc7k t6UOKLlm40k1WHFlP9udiTHXjR4NZLZUWf5HboNkYH5vj9ElfJX2L4PI7PdomVM7mbhh22wRnzMx31pXUS9kMw SvdGemF8VDG9ktb5SGodLduR3J9rj6worwpvX2TUklbrxKQLuZ7VlrGVYrZFr1szk5pjKRrl5Np rvgxvP2a7B2emunOzfYz27B1LfvH b0wveMjmd29 RYGAOBd0eAFAACWvHb86JMvPXOTPxtFN8Mm9e/t22WH6bPM5uPlvEl6h4aJdzORi1ZU7vNz8/1FOt0teen9R9  W1H PakdRB9js foQ8g7qJup5jI3oV87yGsKKuY3zfHzFA0Y5ivLUabFK3hpfvNZrjOPDzq91fYzy2gtW32n8lxLGnwTXvA4I 1dAICPhgYvAACwytuX2nwm357Cm2H9S27No73gc2JPTrtt8aIbZJ2mu7wxDntLDfPe 7WWF76jaXIns6Om9U4xL2iAWH6D6ZXc1xrp9zF5vtRr9xK/1qk91Ma/aALtVvQsMs80iCzf7bTygqRXcpX/zbZvTeLXSgWNL2Y725vk/Ww4PozJ9ViWX94IGqisVh1t/L3UXn3n2ktrJNK4zH8XWYGnWbqRTHtUJX3swvfDNeU67L2mY5aNzVU4tp8zfvQQ6MtYTpMYz8T/kncsR7O79RrSAADYAl9M0mcbAQDAZ6INNZ3DaCDtYXASPLoV3PCfhrfI84exjMwNdudUZHzekufmrXQO5zIe3MuRGRlMNX QQf/CeozK3GT3uma66DZ7Ppf5bCT94Abfl95tR1ZLYJaR6qUST5cdX4G tLtr5g0LZ77XSKRjhrVnTEsfTdRGh66cRuWbm/H6WFm8jvawJ7VZTQ6X5c9 P92M0XYw22S993lX P4Vyl 0fU3hl/su2J S7O/5 HzZq8czcdA148NV2N/PXb72UF96H45dehjISfDcX4Xv94L4iGMzEU9nL7c6beS7PM3ZLhW2X7jvg1GJ5b5Rmfgy20YbtwJeW4b6wv9waMn flWWX7z9DGf8GPY0OfGtdFs0n9d8nBMAgC1AgxcAAMCLeNIeXsrRfdJQAgAAgO3AI40AAAAvoY967T3IiMYuAACArUMPLwAAAAAAAOwUengBAAAAAABgp9DgBQAAAAAAgJ1CgxcAAAAAAAB2Cg1eAAAAAAAA2Ck0eAEAAAAAAGCn0OAFAAAAAACAnUKDFwAAAAAAAHYKDV4AAAAAAADYKTR4AQAAAAAAYKfQ4AUAAAAAAICdQoMXAAAAAAAAdgoNXgAAAAAAANgpNHgBAAAAAABgp9DgBQAAAAAAgJ1CgxcAAAAAAAB2Cg1eAAAAAAAA2Ck0eAEAAAAAAGCn0OAFAAAAAACAnUKDFwAAAAAAAHYKDV4AAAAAAADYKTR4AQAAAAAAYKdsvsGrPpDHxUIWdnq8kbN6lP Gzm4W8jh4hwUDL3V2k479d4x/AO hLoObx Xx 3hzI4 PgygP LjqgySuU nF8X0mN6 aHz8e9Rs2qVr8cX 3m3S/xvt mW7Ootys9c4vhee3xaMQSrtn8w1edx35 p /RP76j3z58iVMrb/ll6G56Y8meSt//PxFvnbuoiFgC/zxs/x0 d2EfxT7Jv30u8h/h297QTnQRrToM4C3Ux8M5Z9/t5bHb vPv6OcxHsffxzfeA93na/B en75U/L P7y06V8j/LX94f8/OU/Yq748EFUqd9ei/oLRarGH/d3u0n3q 731Hno5z i3Kz1zy/xMsNmiHBdZlXYQdv5SONdR1qTr/JL3MRaP5Obx6T19fFmIHHjq936G7Tu2z1m4lZea1z LwB1M4nV0mvmu3m0WnhL1g 8h  P0 iTyvzCZeIzfXFYkh/1oDz/x//If6N8TYU/kABY21f51/KccPdHR75 7YQDVY6/Mz3fxHmPcjNIH5zxOU7PXWeDm7BHdHyDyPGNH0avg8w1lf5IGcV3/At50Osijr9s40Xq snEN7H54RTWb8p5fVxyfV2p/iq//imtHwPZHkKP9FD7YErjz3F/l9uLx97/3N99bK84v gPOnmNpJ2vXyUYvXwCLWkPWMaTiaFBsF6TF9c7wfibdO8w4murLDaezBlrcXNWOG5wc7MwAZLk1c8WNzeD5bAJQBN79STfzPuYXZ5JK9NFyZyMzaqs8br8xePCBG0w7Fo/ifSapHGZlsSepsFjejiIv8fBMiZd eE0NwtzHkimIZFIb5TqwTkkPorNBc2ibh PJpUff/XU9OGpz843SUeaNeh5LZjWHOP2PBzfpPdKqfOTOa/k5mv8RfEYHAvL6yw9FyV58bGStxzStqby s11fey6vtZUVn9Vub4pqx/D634zHE1b12mJvw U3OdXTUX3dzp eT41cfGYiSfu7z5Gyt /b3d yb3u0mQy0uutp qr8PRnx2Qmn/jappQ78semMNLyx9UHy4ouzT5B1oOgj4Nq5QQZpeIDpiT4Kq2fRHp5Sp2QNQUXdFEMa/zlNN5qpV4pPxrmhphE jEp74aq9Pgzx7Beo8XMob964bVy0ZVOHN k90rJdVP tdLK cuO1by41XMWDQ4fNqXqN f1seP6OkqF9VfF65vy lHLEBXLeNR15dwfkD5GKmqwzL /s1IQq5m4ccYvaVtS7v59w/OLhlVug1emASu7zrz2huU5kfjaqrS1f6Wx7n2V73//n8jdVB6/X4bP7abSz5I8xXsnv02 yq8mgkwwiv/4e9gdcQ316N8VldYPvKG7P0w8i/zzX9EwgA/j7o8/5a9//DP9WFehM7n5X1/ /j15R1JrwgsksI3 kJ/tR4nwKaXqt4rXx4XX1z Exm1Urp9 MvXr278jFT/OeufXiD6aZs6zk5 iR9Vi3N/B6U46v0v0iqW6DH4R b1qAwPxtVW2s8Grfia/ o9RUP0hfz768ph5r0nWXRiRJhi/yuS3dUJJl38uwyCYQ/XomdubYJXV1g 8GY3/83 En 86Mvn6y8oz4f/ OpGRHh6u/KWv4kXT1IPnzW94jhx4NXOu0Hc42H9Wte7J17/ zFzQFBx/Ou33Rxn9X3iw1s8G5twXHftr4fjGjzOo pJxc3P66P9q/dXhupz96stLIhyb4KrfXNfHruvrWEH9Vfn6ptjgUd/rEy3gzsw0zb4jFdur6vm1xEpjl8Zf3ODJ/d2H9qPOL3/8JhOznsHgV/Env2Vi7x/i/zow9Vo0aMrQ8B/lz2Ai4mvb5Hb9 mEpr8vfSpfj6Lnc2ONj0M3ZxJc1TdiNcLHS/flscRPNlmZ3KawvBpnlmwrWWka19ZNIayftR5sj3U03HZ/aXTeJ3Sr5YTfw5RR06SeR3ijp cXcnqXOD6vd1cuOv C8FdF3QZwFw3E3 fzzV7brPcc36T2SHZtpYYzb UFMWuez5TkseEQ/GqnHylkU0y947IT0o1OV s11fey6vnbVX2XXN 76UR9HWik/9eMHSa74y9//9v2dVSUlUnUP93fbnHL3n32f/9rzy8oKsvWbPd1qXvBIo64zLkNO/UV8bUf6En0AAAAAAACAOruRR  3lb/qqD1IpZV5VBZbiQYvAAAAAAAA4 xmIf/9n2hAvsul9R64weNC4rfPiL6ri3dcbjUavAAAAAAAALBTtvavNAIAAAAAAAAvQYMXAAAAAAAAdgoNXgAAAAAAANgpNHgBAAAAAABgp2xlg5fXHsqw7UVDP96m1w8AAAAAAICX28K/0uhL77Yu1ycXMo3GpGl Rw7nYzlpXUXj3pJr/S7rl8/zfDk4rkvj6FDk/lxaVy9bMz42bWhtPrfkYhKNALADzDlhaM4Je/p5Lg/jvlxk6niv3ZOuqf/39uYyN/n554Do3PIwkJNUJeGJ3 tKJ1yBzE1 i0pkZ1S5PiiNH68tw8tTCaNDPcjAXN kIqhC/Hl W7oNsxxdkLm OTfXN FUrvg28dluSuPULN8MzR/G0r I58W2e3X8Lb2w/nLEb3t4K6dJZmA Xi1ncfxiqzn2vzs i onz8TOpYmduYzPW7Kcze/Jbccs693uMfFW/N6tqTcy 6 yqD4KPofL HY8lMuoMrHrEL83TNVPfVM/LVdX4fxaJq/ CgT1pFhlNDIxqfeMcXnT7G3iOv 6zt 7RRu8tiaZHbgYtr3cvCT5i96wnTP 9ana l3pheXze2 wbtJHS ZCbNH2vSD2evpvNJw3LYlE lipPQyP62DY86Jha5psvW GU/lBCudrm7ph2PNTeUG9Yc0f1iNJPmlHUtH1gSt vNWYSaUK8ee1zbi2v/C89HhNrvgOr6mS9ftvco1F uHppfEXpFfUX474bQ97C98aDuMtXc6y CVteXLVX3EqiM/S kmXfXubWr7fM/GTiSnS9qagXnnpcZ0bM565f 8tPGuaW3M/v6w7PH/hr1E/VUnZOmxlmTpsyqCxaX9Xu67ze7fLuLa3iev8W3p87FjaskcafWmezqSfbV30tAXyVm5vNQ3F7Iy0VP6tDHttiR9I1Bbg5Xh9TFFb76NhE8TRVLGC9esvAb1hshzz2QRflGe4yue30/nt7AT4zKaTK/n2dCDNoz05bBzLwdOVXE12t4Ud EyuWtprMzqep1P5dh9 jPn1mtx/s473p5nU6ulzhPaAqI1acvUUjch6TtcXtX0eyf8sqsRPGef8XluatTu5uJpo K5wxff0qiUtMy9206brr6tWujfF8dFMRvY1vCN sdtc9ZM8jOW Vjd3f4aJlYaMJDsJttyBdY897IlftfowdZXUDswHT3o6b3DzrsOzZQ8ob78mD6OrpO4w/9Yb2baDt HFr1OaXqV6uXrHRzIzZZjczeToOPly4bl1tVLTmI9Hu86/zuNjh2xVg5fXbkhtfJ3pZuxLr1uXu/6JnJxo6stdvZF08TPazbpct L8E2ldP0uzFwbk5OJEzsfazTrqnji5kJPBQ9AtMdtdNX/9Or4rR7ORnEfL75ugSzoRussnk29yvcxvyV2ts9oohs/tWGNmbP47kv1oFIAdYy6ou0f3cu26/68ltYBeBOlFeNFTitOrkUhDf4S5Nalnbu7uc360wadixU/gsBP94FbxhsCe/6AmNXNWqnRDURjf vhQOH jNsq9SMcOeev6q2r8mvg7mt2lHydaJ36xndatv4rk1k/PEoRg2xO/eSSzu4JAxZbak9OGJPfY/Tupd02MRLlOWld5x1Kbz XBfPa8fanNnqNMUz89z Sw0TbjdUgfDzT3anu19PJfHZ H0jHz5j e6AWN EHMTq5ldnRsxqyr4vm36vXpB7VFDV5h76rULzPKr0vt/lqSDi9Ts8/vZR4NBSe4w0O5jINN02VHDg TgJxe9U2QNJdB0m7U5H5ljxas39AT8uyos1xH1xxcg37UWOYqnzIHU7OblM sHkg5kHsZtK7kqj S2jGtocDOMeeqXrcmozXfHXNQ25O9 IJK3xVhPge/AsbMBZpZqLRaJyZdyPWsJtaPgPjs9Nfi6Me68IZgJo1m9XOM/sK9d3hqrnPOw/lb17J/nPSiXyqN76lc6Y S5 fmTNfgjwJ9Iq uv9aI36AnRKbBonL8Yju9sv5aKqufgoaES3Nvdl/YMIttNZexuR9PemBN5Pq JpU6OU fZWb 8Q7MTfm9uc XIzk Np9nVlfUyYWc3x/J5aXev4cx8mDf4L9JfOp7v8LOOSv8ZtCIH369qdzNjmT98K9w/n3h9elHsjUNXnHvqrXrGg1YfZGbHXBBsrs5T4MDIAgSvxf01sq2a5WvfyIXcQ8yEzD9e5FOt2qXRl96l9odMTrZmtS/zwlqfGqTq6sw9kxlrV3vAewOfanzsPks15nHb0J7Ya96m/ULo/ZSXp7XzsfhS52tE1jwq7R1fWZOialu79h15fGzQq ZUj3AKsxvrrGSmJvKc83cGNhtFqXxbTF3JVfX5gLq6DgagY/vB9dfK/EbC3tC5HbQccQvPpDC/V/MXT9Ng3u8lrnZx2diKp69mjTrh6bKmgSP8x0drfZI0ccC4zqsdaF126z4PPeC IzlPaLom7ItfzAwSV ef7jGKwtSCs6/lc/fH9yWNHh5hb2rZHIX9M5KugiG3U6Tjn ToMVz6HgvVthtul3Qu6tk/UZ7qO/ligqgzcgm3ufxCd1VPu0eOZ/Jt6dw2fqXYvRdTQCAXRe /7Ep18E7GfQsoI/42I 0T67HItY7a9Z9rCJ8DUUyv/Zo0F8t8Tm44kevX zro CRDLtBwjG/9pAfy2lyDeT5Uq/dS/jaJnd8p66fguujU9kra5DDh/Le9Zcrfpe849XHGY3y MW2q7z/c7nrJ3x0e3LajR851MNbH8sraPheMZXZvCa12kMwvT6 qH/GdZZ5p6BVO4nfawTv04q9Lj5dtK4aL1 nFKZzGcfvnKug/Pz7uY6PLybp2 s3SjdwV4r lLGhL4XvWn82czAS6Zjh5Z/o1CBM/qyxzOcyn43SfzrU0PVc1kaZP4nsXn972JParCaHy U/yKB/kTzG6ChfsN74T50 jGU0O5LOqSz/bGj4p1WD7MTyuwEAPiQv yerQw Dk9SjE/oL2 Vp9Aeyc/6kvrLPE lp9KKlK6fR Wnlz/rjQ6tyfVAeP9n4yP5Z8grxZ1/j2Nc/VeLb3Im0m n4zF6bYXu9Pv5CL6 /3PGr9Dq7 awvYI5G2IriFx9A f4vjc y unJzpuH92Nij9PHzHa7x8tHF 57s 8G93JkbqqD/bbm8R0soxbXZ6aeuG3ILLo3D/gmJqJlz82yRyvLrlY/FdF3ayWv7oriUGdOxW48Xstn6jF73EFPblMHQCZuy86/Fa9Pd8UWNHiZnTHsivStAPuhNr1 AAAAAAAAvKWt6OEFAAAAAAAAvJUt iuNAAAAAAAAwOvR4AUAAAAAAICdQoMXAAAAAAAAdgoNXgAAAAAAANgpNHgBAAAAAABgp2xlg5fXHsqw7UVDP96m1w8AAAAAAICX 2LSIvy4LXzp3dbl uRCptGYNM3vyOF8LCetq2jcW3Kt3 Ul5TPzDM08e/p5Lg/jvlxcvWztAIDqPM Xg O6NI4ORe7PpZVT93rtnnRN/t7eXOamfk5N47VleHkqQfUdeJCBOX9MoqGq9bvnt6XbMMvR6cz549ycP3Sq9vBWTpOFB bjdDlLy4ft5oyfWHRt8TCQk4vVXFd UXyZHPF7XemEASpzM39rrfnL469K/GKDnPFn4qPdlMap2b9maP4wlv5Fsu8T fHnrF8rxL/fG6bis2 WnyzFVb5q8Y1NcZwfK9ePBSrEd9vEx1FtL6jbNH7u5UjkuiVUUR/AK JDO7dcZk9O6t3aF14rqmNfXL7Xzv/xaYPX1iQTgIth28vNS5K/6A3bOeNfn6qt35XWK197OFz0/GidnhcNr05HIpFIpHdKfi /7s ON8Op tlrL4Y9PxnOpCr1u9c2y2z7C89Lj9fUHvYWvjW8co5ylY 03ckRP2EK46btF01bnl8WXxpPPSt guE14tMVf874JW02OeIv3F9Jvp 7/1zxaVI2TuLkin8z3625nl7GnucvfCu XOWrEt kzSXn bFS/ViSHPP7PWv9mkwZehrLeXUdafvSK Nj5Xyky1uzfSF7jnvf9Nr2j/drP9n2tGWPNPrSPJ1Jf UXIP0F4FZubzUNxVSGaan8Wxn22hI/kOj3rPH6mKLfWw6bk2g0Vaxg/cEvAMNkOeazOSCiPMNVPr dzm nJ7hqteRiEq1zOpVv9 FHAMBm fWa3H zzglPM6nVs5V8MWf97rWlWbuTi6uJZq 4aqV/rTw msnIOke9tnzYftpDpTZqydVTNCKjNN8RX4HndEZt33qlg2N V/y54hfbbXrVkpbZ92Vc8fka3n5NHkZXSeyZf uN5Pq7SvlK4xsbtdH7H1O3NWr3yfqVKcOFKRNV1Gej9/GmXpleSSvu/aS9x6L7/uC ftl MJTgrUdR/uneoXSi6ZbTxkraJ7x22K4w7PWW67kd9kxJLK9o/wi45v9EtqrBy2s3pDa znSVNjurW5e7/omcnGjqy129IYdRrmo363LdivNPpHX9LE2z09Xk4kTOx9rNPupKPbmQk8FD0K0526Uvf/06vitHs5GcR8vv382s7pPu8snkm1wv81tyV sUB505gLpH93JdpT8mAODHq 1HHyKHneUFR3DBUnQ/lVe/H9SkJvvJRYlj/qPZnbu7frZ82G4l8aMXxQ0ZmZuyaESGK98VX9OrkUhDf8QzF8smr2luAFM/ q0Tn7Gi Ksav/ixnPWXFzyaqvmN2ij1WKIz/qooWf/0eSaHDXMTF4zTxxfN9fVeLX1TWFI Z3xjexTd/1Q9vxYpmt/UbXL/LRrAh/XK Ng7vTTzdtL37Uobv87HMjf/BZ5mweeHQdQgqvnmvn4818co43v8k1RdWNY oY312j5hqjMZnYf5g1lNGst3iL u/aNS 8Qnk9v168cnf9G7zekWmNcN2u5yqJ9vbxcm0DPJXpZ2Ue0tTAgFw0HX65XuqgXrj/OGybLNSXNhDqgwz1W aDg9/21 l pguh/ZNZJEIpFIQSp45EYfeUidL7L1ezZpfl4X 4L6XbvUB eF5bq9RbvdXp6vstNmzx1rl4 03SkTP34vuXZYXkNYcerKd8aXxmXqEbFeKp5c868Tf3nxS9qylIm/dJ7Z92Z/rxN/y1T0SGM25aw/jsFg2b2S6 Sc8rnim7QlSfdTlfufsviskuz5UzGp94BWHL9mHaTNpTXjQ uWMAZKHvXz/KidIf9R18JHGrUsdkwtUzL9yjnRjklX 4Jr a75P1namh5ece qtX8kmj7LTF/AFrVuJsnuRj V6/uaNE0EmAAIemtlf ApX/9ELuIW1PNz6d LdLpJl pyvvQuj2Q2Ol WrX8ftRZbzElYhs1nuc50/wcAbNKe1A6ij7HZc/Qhh56TMj1cnPW7OYclvRKm8lw7kuP4R74lL3gc7G5lAWuWD9stEz/aS315XaO/NutLt60LGFd oCS /Ka5PrEeRTOrl6Ns8JXGZ9X4K4pfbJWc mtpOpWra3MBfHQcjagYf vIWb/2hIjX0brQ2Jrl16M55asU39iote5/yuKzCnv p5kklZe5z4tibPAwlzGP2XxML44Pvc/Pf5G7d1A3Z7m5zM2te 1gjbpDy Jsn3iF917 jtmSBi8veHdW7nsdJncyO2paXRS94ASWPFI4kbvZkQwz78XKCrs1t6XdqMn9SkVWsn6jPdTnXqMC6IsEzAlzHl/Qucrn7UttPpNvT Gy9S8dNY/svwoRvh sKdfBX47Rqbz2537OFgC2xeR6LGK98yW4gbLu2vX8YJ9/gkduljf87vp9etWXsZwm5xjPl3rtXuzXIgW849zHwVzlw3Yrj5/Xc8VXeM XxI  M8mMWnLNXzn CuIXm WKv9T1b3B9eyp7bxifVeLfik7xew2ZjZIbU1f5XPGNTXKfH6vVj570gkfaeplHXR3zT6/kvtaQ9jJ Qq9oTsMPVi0 1tPWxyKjzxqPlw2RwXlLWi1tR7g060vHi6lhlqfAoPHWxGE4WK19otBr2z c838uX0zSrl4bpQHVlZI/pa4vXetaf7Z2YIKuY/9pTT0JJn92WJth57NR5k8Xh u5rI1W/mS3a/0a/LVZTQ6Xy3 QQf9Clu85dJQvWG/0p0/nD2MZmQDtnIqMzQF0Jdk/qRp6GKSfAwYAvD39wyad7EsNlueWkF7EXJ6GEy3fB7mkF 1dOY3OD1rHL/8svlexfrfPIdnzS0TPI81nfcFvNMJSXj5st5L4sdhxmrePS/NL4yu7/kFw85niiM8q8VcWv9gkR/x5Jr Zjo/stbUqij93/epYv2/qUHPBHISeib1Rtm50lq9CfGMzKp0fHfERMPVT8A4mfZeSiY9obMg1fzrfTGHW3zfrT68B26pKfOSz783Twjh6svKDmJSe3EaVmV3HeX5PumZ8MGXO bWofUKqLP 17R/O T PLWjwMsE67Ir0N/VXMTa9fgAAAAAAALylrejhBQAAAAAAALyVrXlpPQAAAAAAAPAWaPACAAAAAADATvlye3u7NY806kvbrveLXiIHAAAAAAAAuNHDCwAAAAAAADuFBi8AAAAAAADslJ1s8JqPz V8PI GfrxNrx8AAAAAAOAz28EGrwcZXR1It/A9YA8yODmRk/NxNPzWXOt3eUH55mM513mWaWCWAgBwmc8f5GE8kPPzk8IfKuZR/slJzo8ZzvrX1OnBvOH8g6J1PJjlxNOZ j earycN0npMlRbPrZU5fN3dG0wKDq7l cXxZfJkYfB XL952vPr1 h Phwxy82yhl/Jj50/8b7bpDe94n8 HPWrxXiPxuf6aVUK19Z/GKTHOev197fVIjvsYmvODY0fnSYKmpbuM5PVeunHA D5XKDVFIv6DvGOW99bF9ub3uL8fm1PB83pXN6GI22PZgLlrL8t/MWL63X3lV96TqWoRXsTDqXp9Hw26m2fpc1y6cV qgml5333T8AsLPMxc/5rLFad2fHm GBdGRZ3Trq3/H5uTw3u2Z6M//cXFz3 2b4Mpnf0AaDkdSlcXQoe5nVj88HUrvsSLK69DmmyvKxxSqdv81 Pe LNI/l213etOX5ZfGl8TQy8dSJ4ikYrlWPT9fx4YpfbJgj/sL91TT7K8x/MMPXK/vPFZ9GUf3qin8z38n1vgy7p2HszR/kYXYoh9HkVcpXGr/YKOf567X3N475tTHlrh6tX5kyDEwZ9ruXQhW1ea7zU7X6qZzGwKzB/t51/0/MZcjp5aU0ajMZmAuT8UO2BdOVv00KeleZE2TqF4SVBmI7P91CrI1wy/Hauqsn32hYW4PTinp3mUo81UKtvyZY87rK9zBO54/X n0DAPBCD3dPcnxk1em1fXm6q14H6/lzeTFt7raOjsOPS aCfPRcD35QyrsZO7UaC9T9twNpWucY5/Lx4T0MwpvA01o0IqM03xFfgVo642lmXec55ncdH674xXbbO71c3kwWccXna8xnT I3o8YuZf69u06un53lqxL/2JiNnr9MbFw/HSfrV6YMHVMmqqgtUnJ qlI/vYp1z5/t4aWNbeE9fdLD7OQ86UEY58f39HF7wnI5Jv7i YJpluuih F7WD7SuHd4ag7yjtRmo7DBJ7OxXfnbYD6 lqd2Q8 HlgcZ9O k3r2V21tNXanfXcskylXj0Z00LuP8W7ls1GRkvqM67NzKsO2J1456nh125Lbni f35DbTAyt//Tq L9/2mzKMlt tH8g0yqtSPjk8ksYy/1LqzxerjWKTi hAiQ44DhYAeB9Ps hDpGr9ay5w t OpWFfn82e5Un0B6Vq8387qKcaEFLylo/tVxI/etF8Lc3lL9pZrnxXfO2dNkWuw0d6zk3e6Pk4/aPdOvEZyx4fMVf8YjOc9Zf24Arzr5 1N0USH874q6Jk/Xu1A5lcx/cc viSuT6ePpsrZ1tx V4Uv9iMovPXa 9viuY3sSHHR9EAtpHz/BQoOf5fS /5zb23tgNkaWObjp8 iTSH4T167 BJrqPWqjg/pu0J2n6wtHcql8O2eOa/QG0/ Oz3aHB9Dyvv8Do87chlQ6Tfym9hdOW/1vSqlVRMzjSI5lJh76qVXw4f7uTpuCFJA/6eHDaO4/AKKthvk4m07OW2LmQySU6oe6ddOfg2ModUaHz9JMcrNXLB g09YA  XSzX0b8W6XWjxjJX dT8Xkb9pHxm9Wl60ASNYVHq7sv1KNsiBgB4c1XrX3OuGfSfpXl5mvpRRHswTCdX5jwwDOc3J9jZff67JOb33 SgXnBnWbB8bDlH/MyepyY ohu21lXw2f6l2ZXvjK/5zFytX8rl5a1JHWnsP8u9FXzrxKdLafxiMyrVX3tyqj8KD4dyLNdrxZ Ta/3mhnN4/E1aLb3 bZkb2mPxV 49i8v3lvGLd1R0/nrt/U3l R/Cd9DFaaVXATbCcX4KFR//P4Lf7Czv4Q/rB GHqjQ h015utD685scD63HefGmVhq8gpe/jUS6ZqPntTC68l8jaP20KyZn6kRzal0Z9q5aO072anLgtXOXnSxrTxrHTxLUkQ8D XbQXPnu5es/lI4ejLpcc0B2j0Uu lVfSm8qYXMQ7Dejk7VJ3eOVs32afqeiX1gBAGuYynO2Oj0oeXYnp/4NXuo9qkkj83jXkjkHJb9K7knt VvORd08eBwsr73AuXx8HJn4SV0X6a/Bfi/1C7YrP1ASXw8jc31hhbNZvXzLBl9pfFY9PorjF1uk7Ppxz9xYNswF7Lf7aETF FtHzvq1p0S8jsuOxtZ fj2XU75ApfoVm7LW assPquw56/tS1J5mfu0KMZ6vidtuklvhUrnp1jR8b8m7bX6I9s757M7cxb1xDO39s/26wTwppYNXvPgPVEDmdUa5oRiPS8fceVv1rywd5Uc1oPeWUkX2HlwACWPFB5K/eCbnDveixV2qxwX9O4qWb hL2UcxAXQDWcOWC  IHSVbz6TJ 9AjqJnmHU/jL4lpVe6fLv8QZfvshsyAEAlh422iHURovWz3UulvP4N3984Ej1vHppbLTMmczGlPYjbcpWcI YPcvd0LPZrkQLz 5zHwdzLx3Z77/O3K77Ce74kvrVHjP0btWt 1/GxlBu/2DRX/KWuX0198zC6kukbxmeV LeiUx4G17LfTF4n4ipf5foVG A f1WrH dR76zB8smcWOn8e6dy/HS98m7qVzSn4Y25zk/vXT 9hfidY3r/fn6RemFREO8tfeprqL3YtJ2hZeI1HY94G1v1VxpfSgOm9K/ mBPcoH8hk6CdSJ PNUF1YYa1Z1fwHi49ifblIpzATOKJd9CUblQBx4LAfG7Kbaa/oWv9 leKng eZLJcvi 9btIF0lW YL1X4bye35bm/je5uBJpL3vZ6UmjL1fR8nWarjZKBkMAgCL6ItHMNYipRONzQ0h/gW5dhRMt3 e4VFL/zs0Fjj7mE Qk/N5tutu6fQ7Inh8ieh7I/vW8ysvHFqt2/rbjdDUGHfml8ZVdfy 4 UxxxGf58RHKjV9sAUf8zU3 KB0f2WtjVRR/7vrVsf7gJjGs4zwTe81s3VilfI74xYZUOn854iNg9u J2b9i9m3q6Rzlmj db6Yw67f aiM2LLv/MuenivVTLn1J/ErlFApjMI6rrDDOata9eTC9JMtb1oHZukef8DLnSs3vSt89P97Ml9vb20X0 YMywa5/Dnljf0J20 sHAAAAAACAbQcavAAAAAAAAIDEykvrAQAAAAAAgI MBi8AAAAAAADslC8m8UgjAAAAAAAAdgY9vAAAAAAAALBTaPACAAAAAADATqHBCwAAAAAAADtlO97hNTRpL/yY8mDSRfgRAIC1eSZdhh XTqJ/s25NKjvvlOX7JjVM0nPZ3KSWSbGeSYfhxxfN3zbpyCTNG5t0ZZKtyvKxGRp/xybp/rs3KbvvlGv/xorir2z/u I/7/rLLkOV48cVf8Tn9qqyf13xqfmn4ccX7f/3zrdjvOz4wsdUdf W1Z81k3QZmq uTZqGHwHsBm3w2nwaZoY9k3qZcSQSiUQirZOqnkv0HOSbVDRtWX47Srquojx7WJeTN03e/DqtPb8O2/PH89rD2eWTNp y 7FofHb/xqko/lz73xX/2Wuv7PJc8 u6dBlx7Oq/9vpd aTNpir7144HHbb3XzZeqgy75rfz9fNr4kvz4mHNs4dJHz9V3b/x Gys67A9fbyMOJ5IJNJOpO17pFF/KdKkLetxK7y2vmvLfJynn7VFP6a/UOmwjtek09tc VXEZYjnj9cfLzculyYdp uM6S/39vp12ix7 TqtvYy3KD8AIJ/WqSOTnoKhVWX5Wj/rr8P6q3LRL8LP0b x/ehf5Zq/btK38GNAy6DjbGXLx3arsn9d8fma/W/3JFTak2edHjC6Li1bHLv6r/ZUjLnysd1c8amx4ooXV3yW5b82vjS J HHIE97WWJ3VNm/RfVnfO6N51e6DF1mHE8AdsJ2NXhpY07cLdqmDV8DkzRPK6dzk/omxQ1CTZO0gtJu2Jq0K6rdKOTKd9EGqplJ8fx3JsV0ufr4SVwuzddxXZNiWplqeeP5dVptBItpWXSZcb5Oaz9i8NryA8Bnpo 72D8oxOcOFf8AYV/02lz5B9G/8Y8S2eXrzaDegOl4TXHjVsw1fx5dRsy1fHw89v51xV V/V8W/zYdr9c6WWXza2OFrj8ep W1r19c di8qvERs MzpvPp/Nn4c8WnK/8t40un0QbdomMJH1ve/i2rP/XcSwMo8ClsV4OXNubo89dFNE8bv7TlPU5awdkna036PgIdp1z5VejJVyvReH49uWqjlC37vLdWonGjlpZBG8Di bMXCzpsV8a6HN0WVb4fAKBYXJ/GSetu/REhpvVvXMfGdWt8kaxc drDQMdpna/L1x8n9J1NMa3D9ddlHa9JGxR0XMw1v4tr fjYXPHn2v u Ldp3Nk/6CnX/HrtorGrZdMyann1R8CYKx btU58lNHY0x991Trx6cp/q/jSZep1uK4Du6do/7rqT5tOEyc6FQA7J/dZxx e9JnpvPFx0mes7ef87eSa15W/TtLnurUc9jLznve230Nwa33O5mn6keUnkUikz56K6lStx8veZ5OXnz0faNJp4nOC/VlT9lxWZX77fJEtg2v5pO1IRfvFtX/tlJf3kv1fFP9VrzVc0702n7TZZO fdeJTk Zn5y Lz7eM3zhl83V5ZWUmfexUdf9mY7colrMxSSKRPnzavnd4vYT IlTUYq9c S7azTruraW/hmkXal2mTX8Rs3 VirvV6jj9tSl dlyXo3m2bPl0Hnudry0/AHxWWpfa9ad ztbfrxE/fmP36NVflfVcoXRd8WOLyn4/jXLNr72H7Xn0XGP3wnEtH9vNtX9dXPu/avxr3OWNX/f40Z4R2mOniCsfP5Zr/7ri075WVZpvz6 fy LTlZ 1bnzFPXXidwLr97PLi4/tNftXz7F6riUegJ33xSRt dosPWHaz9xrt j4Yl9p99IsfaeXNijFtNLTrqpKG5j0JBpXgMqVX0bLp9Pb82u377iMmq8nWH3UUb9HNl8rYPtPNuuydNj ntny6fLW X4AgHx2/Zn3Z8mVPU3enzYvy9fGAn2cIq/ V671u a3zyGushV9P2yGvW9iuo/tR29c 1eVxZ9r/1eJDy2D/phnX3fEyubXm8VO DE3dl352DxXfJTFp9Zd2sj1mvh7r/jSsuljbFnZ wd8TOvsXzvGyupPRXwAO2c7Grw Om3w4iIOAAAAAABgK9Dg9Vp277Tsr7YAAAAAAAD44WjwAgAAAAAAwE7ZjZfWAwAAAAAAABEavAAAAAAAALBTaPACAAAAAADATqHBCwAAAAAAADuFBi8AAAAAAADsFBq8AAAAAAAAsFNo8AIAAAAAAMBOocELAAAAAAAAO4UGLwAAAAAAAOwUGrwAAAAAAACwU2jwAgAAAAAAwE6hwQsAAAAAAAA7hQYvAAAAAAAA7BQavAAAAAAAALBTaPACAAAAAADATqHBCwAAAAAAADuFBi8AAAAAAADsFBq8AAAAAAAAsFNo8AIAAAAAAMBOocELAAAAAAAAO4UGLwAAAAAAAOwUGrwAAAAAAACwU2jwAgAAAAAAwE6hwQsAAAAAAAA7hQYvAAAAAAAA7BQavAAAAAAAALBTaPACAAAAAADATqHBCwAAAAAAADtE5P8DOoBvJ9w5nyMAAAAASUVORK5CYII=[/IMG]

---

### Post by ajgreeny on 2024-04-02
Without any information about the current partitions it is impossible to help you and there are many possible answers once we have more details. You probably need to do this using a live system as it's impossible to work on mounted partitions.

However, please open a terminal and run command 
**sudo fdisk -l**
Copy all the output you see then paste it back here. using code tags please.

See my signature below for a **how-to** for code tags.

---

### Post by mpit52 on 2024-04-02
Sorry about that..I added a picture to the original post but it seems to have not saved. I also don't know why I have so many '\dev\loop#\ disks but that's a different issue.

Output as requested:
```

user@machinename:~$ sudo fdisk -l
[sudo] password for user:
Disk /dev/loop0: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 50 GiB, 53687091200 bytes, 104857600 sectors
Disk model: Virtual disk
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x1821ed67


Device     Boot   Start      End  Sectors  Size Id Type
/dev/sda1  *       2048  1050623  1048576  512M  b W95 FAT32
/dev/sda2       1052670 54468607 53415938 25.5G  5 Extended
_/dev/sda5       1052672 54468607 53415936 25.5G 83 Linux_

plex@Plex-Ubuntu:~$
```

---

### Post by Dennis N on 2024-04-02
The useful part of the output is this:

```
Disk /dev/sda: 50 GiB, 53687091200 bytes, 104857600 sectors
Disk model: Virtual disk
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x1821ed67


Device Boot Start End Sectors Size Id Type
/dev/sda1 * 2048 1050623 1048576 512M b W95 FAT32
/dev/sda2 1052670 54468607 53415938 25.5G 5 Extended
/dev/sda5 1052672 54468607 53415936 25.5G 83 Linux

```

You have a disk with an MS-DOS partition table and have a logical partition sda5 created inside the extended partition sda2. Note that sda2 and sda5 end at the same sector - 54468607. You have to extend sda2 first, then you should be able to extend sda5. Your disk is 50G so you probably had 20G unallocated at the end.

---

### Post by oldfred on 2024-04-02
Please use Code tags. 
How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)


Also removed loop devices, they all are from snap applications.
While I like fdisk and/or parted to see partitions, loops need to be excluded.
You can get most of the info (but less detail on sectors) with this:

lsblk -e 7 -o name,fstype,size,fsused,label,UUID,mountpoint

the -e 7 excludes loops.

---

### Post by mpit52 on 2024-04-02
I gathered as much but when I use 'cfdisk' and select sda2, the option to extend the disk by the free space is not available; it shows a max of 25Gbs. When I highlight sda5, it give me the option to extend the volume but fails :(. 
I recall reading a 'how-to' article that revolves around deleting the disk via fdisk, recreating at the same starting sector but extending the ending sector to the full length of the disk...is this the process that I need to do and if so, do I need to do it for both sda2 and sda5? Assuming order of operations would be delete/extend sda2 (no reboot) and then delete/extend sda5? When I tried to do this on just sda5, the VMGuest wouldn't boot.

With this being a plex server, the easy answer is to simply blow away the VMGuest and rebuild from scratch but I'm trying to use this as a learning experience.

---

### Post by grahammechanical on 2024-04-02
Where do you have the empty/unallocated space? Is it between sda1 and sda2? Or is it after sda5?

We are trying to explain that sda5 is inside sda2 and takes up all the space in sda2. So, you must first enlarge/expand sda2 into unallocated space wherever it is. That would put unallocated space inside sda2. Then you can enlarge/expand sda5 into the unallocated space in sda2. In this way sda5 becomes larger.

Regards


Regards

---

### Post by Dennis N on 2024-04-02
> I gathered as much but when I use 'cfdisk' and select sda2, the option to extend the disk by the free space is not available; it shows a max of 25Gbs. When I highlight sda5, it give me the option to extend the volume but fails...

Are the partitions mounted? You need to do the resizing from the live media (installer) because you cannot resize a mounted partition.

---

### Post by yancek on 2024-04-03
The total sectors output shown from fdisk is almost twice the size of the total sectors for your existing partitions so you need to first (suggested above) unmount the partiiton (sda5) then increase the size of the extended partition (sda2) before increasing the size of sda5.

---

### Post by mpit52 on 2024-04-03
In Vmware, its all a single disk virtual disk. sda1, sd2 and sda5 all live within it. This disk was expanded so logically, its accessible to sda2 which is the is the last disk within Ubunut. If I'm understanding this correctly, sda5 is a virtual disk or 'volume' within sda2..

How does one simply expand the disk? Do I need to use fdisk, delete sda5, delete sda2, recreate at the same starting sector and end at the furthest sector?? If so, I assume I do the same with sda5.

---

### Post by mpit52 on 2024-04-03
thank you. I think this is what I was missing. If I use the live media, is 'cfdisk' available or do I need to use fdisk? If fdisk, do I *delete* the disk and simple recreate it at the same starting sector? Is this what everyone means by "expand".

---

### Post by mpit52 on 2024-04-03
Alright, so I booted into a Live CD and tried to do the following.
1) fdisk /dev/sda
2) p to list all partitions and document sectors
3) d to delete sda2 and sda5
4) n to create a new extended partition (sda2) with the same starting sector size listed in step 2 for sda2 (failed); invalid range. I chose extended because if I select 'primary' the file system type is Linux and not Extended.
5) n to create a new primary partition (sda2) with the same starting sector as sda5; success
6) N to not remove the existing signature 
7) boot and received a "error: no such partition. Entering rescue mode.
8) restore VMGuest snapshot..

---

### Post by mpit52 on 2024-04-03
[duplicate post, delete me please :) ]

---

### Post by Dennis N on 2024-04-04
I didn't notice that this is a virtual disk before post #10. The suggestion about using the installer CD won't work. I had a case like this where expanding a virtual machine partition was done working from the VM. The problem was raised in [this post]("https://ubuntuforums.org/showthread.php?t=2475362&p=14097165#post14097165"). That disk had 21.5 G total, but my root partition 3 ended at 17.2 GB. I wanted to expand it to use the remaining disk space. A method was found using parted, and the bare outline of the steps is in the code block of post #14 of that same thread. However, the partitioning there was GPT. If this method works with an MS-DOS partitioned disk is untested, but I don't see why not.

_Edit_: Tested, and this procedure works with an MS-DOS partitioned disk, resizing the extended-partition then the logical partition.

---

### Post by TheFu on 2024-04-04
So, the "best" answer is not to use MS-DOS/MBR partitioning.  Doing so, brings all the old limitations and workarounds that came with HDD partitioning since the 1980s.  Only 4 primary partitions are allowed.  1 of those primary partitions can be an "extended" partition which can hold a bunch of "Logical Partitions", assuming every single logical partition fits inside the "extended partition".   You can read up on each of these things in the wikipedia articles.  Anyone over 30 that setup HDDs probably has all of this memorized.  We had to live with it for decades.

So, you decide not to use DOS/MBR partitioning. What should you use?  **GUID Partitioning** - also called **GPT**.  You can read up on it at wikipedia.  It removes the needs for workarounds. It supports huge HDDs, it doesn't place the primary and backup partition table next to each other. One is at the start of the storage and the other is at the end. This should drastically reduce the chance that both copies of the GPT become corrupted - they aren't anywhere near each other.  Additionally, GPT disks can have over 100 primary partitions, so the prior limit of 4 is gone.  All partitions are primary in GPT.

A little more history.  fdisk and fdisk-based tools didn't support GPT for many years. If you use old versions from around 2010, they won't work.  Other tools, based on "parted" were used and still exist.  **gparted** is the GUI partitioning tool which is very capable and popular across all Linux systems. Both parted and gparted support both DOS and GPT partitioning.  If you are working on a server that doesn't have any GUI, sometimes it is easier to do partitioning of the disk from a _Try Ubuntu_  ISO environment BEFORE doing the install.  Partitioning inside the Ubuntu Installers has always sucked.

Sadly, disk partitions still cannot be modified while file systems inside are mounted regardless, so we still need to boot from alternate media to make changes.  There are ways around this using volume management tools, but those are mainly for IT professionals due to the complexity and capabilities provided.

In summary. Start over. Ensure that GPT is used. Then the legacy DOS/MBR partitioning workarounds won't happen.  You'll be able to extend the VM storage and then extend the last partition inside that storage easily.  Use gparted to get a nice visual image of the disk involved.  

Lastly, if you are using SSDs, remember that all storage locations are virtual and have nothing to do with the actual chips used to hold our data.

---

### Post by yancek on 2024-04-04
Your fdisk output from post 3 shows that you configured the virtual drive using only 50% of the available space.  You can see that by checking total sectors and the sectors used for sda2 and sda5.  Why did you not use all the space?  If you don't have any data on it just do it over and use the entire disk.

>   I chose extended because if I select 'primary' the file system type is Linux and not Extended.

Why would you want an Extended partition?  There is no point to it and the partition on which you actually install Ubuntu if you do this will be sda5 and a logical partition and will have a file system type of Linux which is what is needed.  The suggestion to use a GPT disk label is recommended although it is possible to do an EFI install of Linux on a dos disk there really is no reason to do it and it is not recommended.

Are you doing this just to learn about partitioning and resizing?  If not, there is no reason to do anything more than recreate the virtual device.

---

### Post by TheFu on 2024-04-04
> **yancek said:**
>  The suggestion to use a GPT disk label is recommended although it is possible to do an EFI install of Linux on a dos disk there really is no reason to do it and it is not recommended. 

Odd. I've been using GPT with BIOS booting for over a decade.  It is only MSFT that arbitrarily made EFI + GPT required.  Linux doesn't care and has supported every mix+match of GPT/MBR and UEFI/Legacy Boot.   Around 2010, some non-standard hardware didn't like that, but it was a bug in the BIOS, not a Linux restriction.

Basically, always use GPT with all disks on Linux regardless of boot method has worked since around 2014 hardware.  Well ... maybe some really, really, cheap systems from HP or Acer didn't support this, but I've never had an issue.

---

### Post by Dennis N on 2024-04-04
> Sadly, disk partitions still cannot be modified while file systems inside are mounted regardless, so we still need to boot from alternate media to make changes. 
A partition (including root) actually can be resized while in use if you follow the procedure outlined [here]("https://ubuntuforums.org/showthread.php?t=2475362&p=14098104#post14098104").

---

### Post by yancek on 2024-04-04
>  Odd. I've been using GPT with BIOS booting for over a decade.  It is  only MSFT that arbitrarily made EFI + GPT required.  Linux doesn't care  and has supported every mix+match of GPT/MBR and UEFI/Legacy Boot.    Around 2010, some non-standard hardware didn't like that, but it was a  bug in the BIOS, not a Linux restriction.

Obviously that can be done and I have an old release of Ubuntu installed in Legacy mode on an external drive  flash drive that is gpt as well as an EFI install on a dos drive.  It is generally 'suggested' or 'recommended' (particularly to new users) to do EFI on GPT.

---

