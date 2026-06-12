---
title: "how do i turn of mtrr in the Xorg.conf"
date: 2007-11-20
forum: General Help
---

### Post by zivxx on 2007-11-20
hey guys..i need to turn MTRR off in my xorg.conf to fix something my graphics..
first..i don't know whats xorg.conf or how to enter it...would be really nice if someone know
second...how do i turn MTRR off inside it?

---

### Post by zivxx on 2007-11-24
any ideas?
ive been trying for 3 days and can't find a normal guide on google :/

---

### Post by gmaniac on 2007-11-24
I haven't tested it myself

At a terminal
```
sudo gedit /etc/X11/xorg.conf
```between section "device" and the end section add this line
```
         Option      "mtrr" "off" 
```


But are you sure you want to disable this? How you came to this conclusion?

---

### Post by zivxx on 2007-11-24
ok, i think i havn't gave enough information, here goes

qoute from [http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#ATI](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#ATI) ,

"    *  Radeon X300 (PCIE)
          o Chipset: RV370 5B60
          o Driver: ati-drivers-8.22.5
          o Notes: Random lockups can be fixed by turning off mtrr in Xorg.conf"

i think that "random lockups" might be the lags i have

Edit: I have turned it off..its not the problem

---

### Post by gmaniac on 2007-11-24
These lockups when they appear?
Have you seen anything interesting with the **dmesg** comand?
I found this long thread, have you seen it?
[http://ubuntuforums.org/showthread.php?t=585714&page=3](http://ubuntuforums.org/showthread.php?t=585714&page=3)

---

### Post by zivxx on 2007-11-24
i don't think when they said "lockups" they meant for lags, so thats probably not my problem, 
would you go to [http://ubuntuforums.org/showthread.php?t=614648](http://ubuntuforums.org/showthread.php?t=614648) and have a short look at this thread?i explain my problem there and you can see what ive tried so far and nothing works.
thanks for your time.

---

### Post by gmaniac on 2007-11-24
I skimmed through the thread but i didn't see any useful information.
Could you see/post the output of the following commands?
Maybe there is something interesting there.
```

dmesg
cat /var/log/Xorg.0.log
glxinfo
fglrxinfo

```Are you using compiz by any chance? You could try disabling it.

---

### Post by zivxx on 2007-11-24
about compiz, not that i know of

about the command/s(?) is it one or a few commands, if its a few...each line its 1 command or..?

---

### Post by gmaniac on 2007-11-24
Check the compiz first,
System -> preferences -> appearance -> Visual effects
Select "none" .

About the commands they are one liners

---

### Post by zivxx on 2007-11-24
here goes, its not about the effects and for the commands:

dmesg:
[ 3892.334497] eth1: Tx timeout - resetting
[ 3894.621715] eth1: Tx timeout - resetting
[ 3896.617696] eth1: Tx timeout - resetting
[ 3898.673583] eth1: Tx timeout - resetting
[ 3900.960790] eth1: Tx timeout - resetting
[ 3902.976824] eth1: Tx timeout - resetting
[ 3905.264227] eth1: Tx timeout - resetting
[ 3907.555243] eth1: Tx timeout - resetting
[ 3909.842658] eth1: Tx timeout - resetting
[ 3912.129819] eth1: Tx timeout - resetting
[ 3914.421117] eth1: Tx timeout - resetting
[ 3916.417028] eth1: Tx timeout - resetting
[ 3918.708689] eth1: Tx timeout - resetting
[ 3920.999619] eth1: Tx timeout - resetting
[ 3923.282953] eth1: Tx timeout - resetting
[ 3925.570374] eth1: Tx timeout - resetting
[ 3927.773912] eth1: Tx timeout - resetting
[ 3930.065071] eth1: Tx timeout - resetting
[ 3932.356341] eth1: Tx timeout - resetting
[ 3934.647786] eth1: Tx timeout - resetting
[ 3936.939070] eth1: Tx timeout - resetting
[ 3939.226295] eth1: Tx timeout - resetting
[ 3941.517641] eth1: Tx timeout - resetting
[ 3943.805174] eth1: Tx timeout - resetting
[ 3945.896575] eth1: Tx timeout - resetting
[ 3948.188044] eth1: Tx timeout - resetting
[ 3950.479187] eth1: Tx timeout - resetting
[ 3952.770590] eth1: Tx timeout - resetting
[ 3955.061955] eth1: Tx timeout - resetting
[ 3957.077657] eth1: Tx timeout - resetting
[ 3959.364957] eth1: Tx timeout - resetting
[ 3961.652275] eth1: Tx timeout - resetting
[ 3963.943608] eth1: Tx timeout - resetting
[ 3966.151091] eth1: Tx timeout - resetting
[ 3968.438399] eth1: Tx timeout - resetting
[ 3970.454227] eth1: Tx timeout - resetting
[ 3972.745511] eth1: Tx timeout - resetting
[ 3974.769893] eth1: Tx timeout - resetting
[ 3977.060688] eth1: Tx timeout - resetting
[ 3979.351983] eth1: Tx timeout - resetting
[ 3981.359855] eth1: Tx timeout - resetting
[ 3983.651182] eth1: Tx timeout - resetting
[ 3985.938578] eth1: Tx timeout - resetting
[ 3988.225935] eth1: Tx timeout - resetting
[ 3990.513119] eth1: Tx timeout - resetting
[ 3992.804405] eth1: Tx timeout - resetting
[ 3994.996052] eth1: Tx timeout - resetting
[ 3997.231493] eth1: Tx timeout - resetting
[ 3999.498797] eth1: Tx timeout - resetting
[ 4001.785980] eth1: Tx timeout - resetting
[ 4003.781868] eth1: Tx timeout - resetting
[ 4005.778048] eth1: Tx timeout - resetting
[ 4008.069204] eth1: Tx timeout - resetting
[ 4010.096936] eth1: Tx timeout - resetting
[ 4012.356312] eth1: Tx timeout - resetting
[ 4014.384256] eth1: Tx timeout - resetting
[ 4016.643591] eth1: Tx timeout - resetting
[ 4018.675342] eth1: Tx timeout - resetting
[ 4020.966636] eth1: Tx timeout - resetting
[ 4022.962602] eth1: Tx timeout - resetting
[ 4025.018348] eth1: Tx timeout - resetting
[ 4027.309633] eth1: Tx timeout - resetting
[ 4029.601267] eth1: Tx timeout - resetting
[ 4031.888418] eth1: Tx timeout - resetting
[ 4033.900230] eth1: Tx timeout - resetting
[ 4035.940105] eth1: Tx timeout - resetting
[ 4038.199311] eth1: Tx timeout - resetting
[ 4040.203206] eth1: Tx timeout - resetting
[ 4042.262980] eth1: Tx timeout - resetting
[ 4044.258893] eth1: Tx timeout - resetting
[ 4046.546184] eth1: Tx timeout - resetting
[ 4048.542091] eth1: Tx timeout - resetting
[ 4050.833592] eth1: Tx timeout - resetting
[ 4052.833286] eth1: Tx timeout - resetting
[ 4055.128604] eth1: Tx timeout - resetting
[ 4057.420191] eth1: Tx timeout - resetting
[ 4059.711651] eth1: Tx timeout - resetting
[ 4062.002533] eth1: Tx timeout - resetting
[ 4064.293866] eth1: Tx timeout - resetting
[ 4066.581232] eth1: Tx timeout - resetting
[ 4068.872502] eth1: Tx timeout - resetting
[ 4071.163788] eth1: Tx timeout - resetting
[ 4073.451390] eth1: Tx timeout - resetting
[ 4075.742422] eth1: Tx timeout - resetting
[ 4078.033890] eth1: Tx timeout - resetting
[ 4080.321025] eth1: Tx timeout - resetting
[ 4082.608779] eth1: Tx timeout - resetting
[ 4084.899740] eth1: Tx timeout - resetting
[ 4087.186890] eth1: Tx timeout - resetting
[ 4089.294751] eth1: Tx timeout - resetting
[ 4091.585958] eth1: Tx timeout - resetting
[ 4093.873291] eth1: Tx timeout - resetting
[ 4096.160482] eth1: Tx timeout - resetting
[ 4098.451855] eth1: Tx timeout - resetting
[ 4100.739056] eth1: Tx timeout - resetting
[ 4103.030377] eth1: Tx timeout - resetting
[ 4105.026284] eth1: Tx timeout - resetting
[ 4107.022192] eth1: Tx timeout - resetting
[ 4109.018099] eth1: Tx timeout - resetting
[ 4111.014006] eth1: Tx timeout - resetting
[ 4113.009913] eth1: Tx timeout - resetting
[ 4115.005821] eth1: Tx timeout - resetting
[ 4117.001729] eth1: Tx timeout - resetting
[ 4118.997636] eth1: Tx timeout - resetting
[ 4120.993543] eth1: Tx timeout - resetting
[ 4122.989450] eth1: Tx timeout - resetting
[ 4124.985358] eth1: Tx timeout - resetting
[ 4126.981257] eth1: Tx timeout - resetting
[ 4128.977164] eth1: Tx timeout - resetting
[ 4130.973072] eth1: Tx timeout - resetting
[ 4132.968979] eth1: Tx timeout - resetting
[ 4134.964886] eth1: Tx timeout - resetting
[ 4136.960794] eth1: Tx timeout - resetting
[ 4138.956701] eth1: Tx timeout - resetting
[ 4140.952608] eth1: Tx timeout - resetting
[ 4142.948516] eth1: Tx timeout - resetting
[ 4144.944423] eth1: Tx timeout - resetting
[ 4146.940330] eth1: Tx timeout - resetting
[ 4148.936237] eth1: Tx timeout - resetting
[ 4150.932145] eth1: Tx timeout - resetting
[ 4152.928052] eth1: Tx timeout - resetting
[ 4154.923959] eth1: Tx timeout - resetting
[ 4156.919867] eth1: Tx timeout - resetting
[ 4158.915774] eth1: Tx timeout - resetting
[ 4160.911681] eth1: Tx timeout - resetting
[ 4162.907596] eth1: Tx timeout - resetting
[ 4164.903503] eth1: Tx timeout - resetting
[ 4166.899411] eth1: Tx timeout - resetting
[ 4168.895318] eth1: Tx timeout - resetting
[ 4170.891225] eth1: Tx timeout - resetting
[ 4172.887132] eth1: Tx timeout - resetting
[ 4174.883040] eth1: Tx timeout - resetting
[ 4176.878947] eth1: Tx timeout - resetting
[ 4178.874854] eth1: Tx timeout - resetting
[ 4180.870762] eth1: Tx timeout - resetting
[ 4182.866668] eth1: Tx timeout - resetting
[ 4184.862576] eth1: Tx timeout - resetting
[ 4186.858483] eth1: Tx timeout - resetting
[ 4188.854391] eth1: Tx timeout - resetting
[ 4190.850298] eth1: Tx timeout - resetting
[ 4192.846205] eth1: Tx timeout - resetting
[ 4194.842112] eth1: Tx timeout - resetting
[ 4196.838019] eth1: Tx timeout - resetting
[ 4198.833926] eth1: Tx timeout - resetting
[ 4200.829834] eth1: Tx timeout - resetting
[ 4202.825742] eth1: Tx timeout - resetting
[ 4204.821648] eth1: Tx timeout - resetting
[ 4206.817556] eth1: Tx timeout - resetting
[ 4208.813463] eth1: Tx timeout - resetting
[ 4210.809370] eth1: Tx timeout - resetting
[ 4212.805278] eth1: Tx timeout - resetting
[ 4214.801185] eth1: Tx timeout - resetting
[ 4216.797093] eth1: Tx timeout - resetting
[ 4219.088422] eth1: Tx timeout - resetting
[ 4221.379761] eth1: Tx timeout - resetting
[ 4223.671205] eth1: Tx timeout - resetting
[ 4225.958403] eth1: Tx timeout - resetting
[ 4228.245681] eth1: Tx timeout - resetting
[ 4230.536999] eth1: Tx timeout - resetting
[ 4232.824625] eth1: Tx timeout - resetting
[ 4234.836090] eth1: Tx timeout - resetting
[ 4237.127493] eth1: Tx timeout - resetting
[ 4239.418794] eth1: Tx timeout - resetting
[ 4241.706151] eth1: Tx timeout - resetting
[ 4243.718002] eth1: Tx timeout - resetting
[ 4245.757924] eth1: Tx timeout - resetting
[ 4248.041327] eth1: Tx timeout - resetting
[ 4250.056884] eth1: Tx timeout - resetting
[ 4252.344202] eth1: Tx timeout - resetting
[ 4254.627703] eth1: Tx timeout - resetting
[ 4256.918964] eth1: Tx timeout - resetting
[ 4259.210218] eth1: Tx timeout - resetting
[ 4261.497726] eth1: Tx timeout - resetting
[ 4263.789011] eth1: Tx timeout - resetting
[ 4265.788911] eth1: Tx timeout - resetting
[ 4267.840481] eth1: Tx timeout - resetting
[ 4270.076270] eth1: Tx timeout - resetting
[ 4272.363263] eth1: Tx timeout - resetting
[ 4274.646597] eth1: Tx timeout - resetting
[ 4276.937765] eth1: Tx timeout - resetting
[ 4279.229185] eth1: Tx timeout - resetting
[ 4281.516653] eth1: Tx timeout - resetting
[ 4283.708055] eth1: Tx timeout - resetting
[ 4285.995547] eth1: Tx timeout - resetting
[ 4288.282548] eth1: Tx timeout - resetting
[ 4290.569898] eth1: Tx timeout - resetting
[ 4292.861184] eth1: Tx timeout - resetting
[ 4295.148525] eth1: Tx timeout - resetting
[ 4297.236150] eth1: Tx timeout - resetting
[ 4299.527474] eth1: Tx timeout - resetting
[ 4301.535444] eth1: Tx timeout - resetting
[ 4303.579254] eth1: Tx timeout - resetting
[ 4305.830509] eth1: Tx timeout - resetting
[ 4307.878556] eth1: Tx timeout - resetting
[ 4310.134026] eth1: Tx timeout - resetting
[ 4312.420997] eth1: Tx timeout - resetting
[ 4314.712328] eth1: Tx timeout - resetting
[ 4317.003600] eth1: Tx timeout - resetting
[ 4319.295012] eth1: Tx timeout - resetting
[ 4321.490413] eth1: Tx timeout - resetting
[ 4323.777866] eth1: Tx timeout - resetting
[ 4326.065588] eth1: Tx timeout - resetting
[ 4328.080925] eth1: Tx timeout - resetting
[ 4330.352231] eth1: Tx timeout - resetting
[ 4332.643569] eth1: Tx timeout - resetting
[ 4334.643432] eth1: Tx timeout - resetting
[ 4336.934777] eth1: Tx timeout - resetting
[ 4339.222117] eth1: Tx timeout - resetting
[ 4341.513364] eth1: Tx timeout - resetting
[ 4343.800904] eth1: Tx timeout - resetting
[ 4346.092443] eth1: Tx timeout - resetting
[ 4348.139755] eth1: Tx timeout - resetting
[ 4350.431125] eth1: Tx timeout - resetting
[ 4352.722521] eth1: Tx timeout - resetting
[ 4355.005673] eth1: Tx timeout - resetting
[ 4357.292979] eth1: Tx timeout - resetting
[ 4359.584371] eth1: Tx timeout - resetting
[ 4361.871681] eth1: Tx timeout - resetting
[ 4364.162895] eth1: Tx timeout - resetting
[ 4366.218791] eth1: Tx timeout - resetting
[ 4368.450333] eth1: Tx timeout - resetting
[ 4370.737651] eth1: Tx timeout - resetting
[ 4373.024804] eth1: Tx timeout - resetting
[ 4375.296225] eth1: Tx timeout - resetting
[ 4377.471605] eth1: Tx timeout - resetting
[ 4379.754963] eth1: Tx timeout - resetting
[ 4382.042244] eth1: Tx timeout - resetting
[ 4384.333582] eth1: Tx timeout - resetting
[ 4386.620923] eth1: Tx timeout - resetting
[ 4388.648688] eth1: Tx timeout - resetting
[ 4390.908292] eth1: Tx timeout - resetting
[ 4392.987837] eth1: Tx timeout - resetting
[ 4395.275186] eth1: Tx timeout - resetting
[ 4397.566471] eth1: Tx timeout - resetting
[ 4399.857820] eth1: Tx timeout - resetting
[ 4402.145217] eth1: Tx timeout - resetting
[ 4404.161099] eth1: Tx timeout - resetting
[ 4406.452179] eth1: Tx timeout - resetting
[ 4408.456086] eth1: Tx timeout - resetting
[ 4410.743383] eth1: Tx timeout - resetting
[ 4413.034684] eth1: Tx timeout - resetting
[ 4415.030613] eth1: Tx timeout - resetting
[ 4417.026497] eth1: Tx timeout - resetting
[ 4419.022405] eth1: Tx timeout - resetting
[ 4421.018373] eth1: Tx timeout - resetting
[ 4423.074245] eth1: Tx timeout - resetting
[ 4425.317787] eth1: Tx timeout - resetting
[ 4427.600940] eth1: Tx timeout - resetting
[ 4429.892266] eth1: Tx timeout - resetting
[ 4432.151734] eth1: Tx timeout - resetting
[ 4434.375143] eth1: Tx timeout - resetting
[ 4436.454681] eth1: Tx timeout - resetting
[ 4438.745975] eth1: Tx timeout - resetting
[ 4441.033272] eth1: Tx timeout - resetting
[ 4443.324582] eth1: Tx timeout - resetting
[ 4445.320470] eth1: Tx timeout - resetting
[ 4447.316381] eth1: Tx timeout - resetting
[ 4449.312298] eth1: Tx timeout - resetting
[ 4451.308210] eth1: Tx timeout - resetting
[ 4453.304124] eth1: Tx timeout - resetting
[ 4455.300022] eth1: Tx timeout - resetting
[ 4457.343827] eth1: Tx timeout - resetting
[ 4459.635122] eth1: Tx timeout - resetting
[ 4461.926439] eth1: Tx timeout - resetting
[ 4463.922389] eth1: Tx timeout - resetting
[ 4466.213737] eth1: Tx timeout - resetting
[ 4468.505016] eth1: Tx timeout - resetting
[ 4470.796246] eth1: Tx timeout - resetting
[ 4473.083549] eth1: Tx timeout - resetting
[ 4475.374853] eth1: Tx timeout - resetting
[ 4477.554374] eth1: Tx timeout - resetting
[ 4479.845768] eth1: Tx timeout - resetting
[ 4482.137157] eth1: Tx timeout - resetting
[ 4484.424403] eth1: Tx timeout - resetting
[ 4486.715604] eth1: Tx timeout - resetting
[ 4488.727485] eth1: Tx timeout - resetting
[ 4490.723392] eth1: Tx timeout - resetting
[ 4492.719553] eth1: Tx timeout - resetting
[ 4495.006594] eth1: Tx timeout - resetting
[ 4497.234191] eth1: Tx timeout - resetting
[ 4499.525320] eth1: Tx timeout - resetting
[ 4501.569130] eth1: Tx timeout - resetting
[ 4503.565036] eth1: Tx timeout - resetting
[ 4505.856402] eth1: Tx timeout - resetting
[ 4507.852362] eth1: Tx timeout - resetting
[ 4509.924005] eth1: Tx timeout - resetting
[ 4511.919899] eth1: Tx timeout - resetting
[ 4514.211231] eth1: Tx timeout - resetting
[ 4516.502508] eth1: Tx timeout - resetting
[ 4518.793839] eth1: Tx timeout - resetting
[ 4521.081173] eth1: Tx timeout - resetting
[ 4523.372586] eth1: Tx timeout - resetting
[ 4525.663839] eth1: Tx timeout - resetting
[ 4527.659635] eth1: Tx timeout - resetting
[ 4529.946931] eth1: Tx timeout - resetting
[ 4532.238391] eth1: Tx timeout - resetting
[ 4534.525677] eth1: Tx timeout - resetting
[ 4536.812993] eth1: Tx timeout - resetting
[ 4538.924592] eth1: Tx timeout - resetting
[ 4541.116075] eth1: Tx timeout - resetting
[ 4543.375490] eth1: Tx timeout - resetting
[ 4545.666727] eth1: Tx timeout - resetting
[ 4547.958060] eth1: Tx timeout - resetting
[ 4550.245346] eth1: Tx timeout - resetting
[ 4552.257197] eth1: Tx timeout - resetting
[ 4554.548548] eth1: Tx timeout - resetting
[ 4556.544461] eth1: Tx timeout - resetting
[ 4558.540472] eth1: Tx timeout - resetting
[ 4560.596137] eth1: Tx timeout - resetting
[ 4562.839499] eth1: Tx timeout - resetting
[ 4565.122824] eth1: Tx timeout - resetting
[ 4567.414173] eth1: Tx timeout - resetting
[ 4569.705435] eth1: Tx timeout - resetting
[ 4571.725300] eth1: Tx timeout - resetting
[ 4574.016705] eth1: Tx timeout - resetting
[ 4576.307929] eth1: Tx timeout - resetting
[ 4578.339809] eth1: Tx timeout - resetting
[ 4580.371540] eth1: Tx timeout - resetting
[ 4582.662851] eth1: Tx timeout - resetting
[ 4584.954142] eth1: Tx timeout - resetting
[ 4586.954074] eth1: Tx timeout - resetting
[ 4589.005843] eth1: Tx timeout - resetting
[ 4591.237386] eth1: Tx timeout - resetting
[ 4593.293113] eth1: Tx timeout - resetting
[ 4595.584349] eth1: Tx timeout - resetting
[ 4597.879640] eth1: Tx timeout - resetting
[ 4600.170962] eth1: Tx timeout - resetting
[ 4602.166860] eth1: Tx timeout - resetting
[ 4604.454190] eth1: Tx timeout - resetting
[ 4606.745471] eth1: Tx timeout - resetting
[ 4609.036776] eth1: Tx timeout - resetting
[ 4611.260233] eth1: Tx timeout - resetting
[ 4613.547521] eth1: Tx timeout - resetting
[ 4615.838829] eth1: Tx timeout - resetting
[ 4618.130130] eth1: Tx timeout - resetting
[ 4620.413440] eth1: Tx timeout - resetting
[ 4622.648851] eth1: Tx timeout - resetting
[ 4624.932184] eth1: Tx timeout - resetting
[ 4626.928092] eth1: Tx timeout - resetting
[ 4629.215390] eth1: Tx timeout - resetting
[ 4631.506712] eth1: Tx timeout - resetting
[ 4633.510592] eth1: Tx timeout - resetting
[ 4635.506498] eth1: Tx timeout - resetting
[ 4637.789809] eth1: Tx timeout - resetting
[ 4640.081114] eth1: Tx timeout - resetting
[ 4642.372415] eth1: Tx timeout - resetting
[ 4644.663724] eth1: Tx timeout - resetting
[ 4646.659615] eth1: Tx timeout - resetting
[ 4648.950960] eth1: Tx timeout - resetting
[ 4650.946891] eth1: Tx timeout - resetting
[ 4653.002621] eth1: Tx timeout - resetting
[ 4655.293915] eth1: Tx timeout - resetting
[ 4657.585211] eth1: Tx timeout - resetting
[ 4659.581140] eth1: Tx timeout - resetting
[ 4661.872442] eth1: Tx timeout - resetting
[ 4663.900298] eth1: Tx timeout - resetting
[ 4666.191566] eth1: Tx timeout - resetting
[ 4668.187477] eth1: Tx timeout - resetting
[ 4670.474779] eth1: Tx timeout - resetting
[ 4672.470702] eth1: Tx timeout - resetting
[ 4674.466608] eth1: Tx timeout - resetting
[ 4676.757956] eth1: Tx timeout - resetting
[ 4678.753857] eth1: Tx timeout - resetting
[ 4680.749762] eth1: Tx timeout - resetting
[ 4683.037167] eth1: Tx timeout - resetting
[ 4685.328337] eth1: Tx timeout - resetting
[ 4687.340218] eth1: Tx timeout - resetting
[ 4689.376035] eth1: Tx timeout - resetting
[ 4691.387903] eth1: Tx timeout - resetting
[ 4693.423721] eth1: Tx timeout - resetting
[ 4695.419642] eth1: Tx timeout - resetting
[ 4697.667021] eth1: Tx timeout - resetting
[ 4699.958327] eth1: Tx timeout - resetting
[ 4701.982193] eth1: Tx timeout - resetting
[ 4704.034009] eth1: Tx timeout - resetting
[ 4706.073779] eth1: Tx timeout - resetting
[ 4708.365090] eth1: Tx timeout - resetting
[ 4710.656400] eth1: Tx timeout - resetting
[ 4712.947704] eth1: Tx timeout - resetting
[ 4714.943602] eth1: Tx timeout - resetting
[ 4717.234997] eth1: Tx timeout - resetting
[ 4719.522228] eth1: Tx timeout - resetting
[ 4721.617913] eth1: Tx timeout - resetting
[ 4723.613809] eth1: Tx timeout - resetting
[ 4725.609746] eth1: Tx timeout - resetting
[ 4727.901101] eth1: Tx timeout - resetting
[ 4730.192434] eth1: Tx timeout - resetting
[ 4732.479823] eth1: Tx timeout - resetting
[ 4734.770959] eth1: Tx timeout - resetting
[ 4737.058308] eth1: Tx timeout - resetting
[ 4739.193880] eth1: Tx timeout - resetting
[ 4741.485168] eth1: Tx timeout - resetting
[ 4743.776477] eth1: Tx timeout - resetting
[ 4745.868227] eth1: Tx timeout - resetting
[ 4748.155490] eth1: Tx timeout - resetting
[ 4750.151443] eth1: Tx timeout - resetting
[ 4752.438705] eth1: Tx timeout - resetting
[ 4754.730006] eth1: Tx timeout - resetting
[ 4756.729978] eth1: Tx timeout - resetting
[ 4759.017282] eth1: Tx timeout - resetting
[ 4761.308534] eth1: Tx timeout - resetting
[ 4763.595831] eth1: Tx timeout - resetting
[ 4765.887152] eth1: Tx timeout - resetting
[ 4768.174448] eth1: Tx timeout - resetting
[ 4770.461750] eth1: Tx timeout - resetting
[ 4772.753049] eth1: Tx timeout - resetting
[ 4774.872790] eth1: Tx timeout - resetting
[ 4777.164020] eth1: Tx timeout - resetting
[ 4779.451378] eth1: Tx timeout - resetting
[ 4781.495258] eth1: Tx timeout - resetting
[ 4783.782457] eth1: Tx timeout - resetting
[ 4785.798342] eth1: Tx timeout - resetting
[ 4788.089633] eth1: Tx timeout - resetting
[ 4790.380927] eth1: Tx timeout - resetting
[ 4792.664443] eth1: Tx timeout - resetting
[ 4794.955570] eth1: Tx timeout - resetting
[ 4796.963485] eth1: Tx timeout - resetting
[ 4799.254714] eth1: Tx timeout - resetting
[ 4801.542027] eth1: Tx timeout - resetting
[ 4803.833412] eth1: Tx timeout - resetting
[ 4806.032817] eth1: Tx timeout - resetting
[ 4808.028730] eth1: Tx timeout - resetting
[ 4810.084523] eth1: Tx timeout - resetting
[ 4812.375904] eth1: Tx timeout - resetting
[ 4814.579370] eth1: Tx timeout - resetting
[ 4816.866617] eth1: Tx timeout - resetting
[ 4819.154124] eth1: Tx timeout - resetting
[ 4821.441222] eth1: Tx timeout - resetting
[ 4823.732540] eth1: Tx timeout - resetting
[ 4825.728445] eth1: Tx timeout - resetting
[ 4828.019788] eth1: Tx timeout - resetting
[ 4830.015699] eth1: Tx timeout - resetting
[ 4832.306996] eth1: Tx timeout - resetting
[ 4834.594251] eth1: Tx timeout - resetting
[ 4836.885694] eth1: Tx timeout - resetting
[ 4839.172885] eth1: Tx timeout - resetting
[ 4841.460180] eth1: Tx timeout - resetting
[ 4843.460093] eth1: Tx timeout - resetting
[ 4845.511871] eth1: Tx timeout - resetting
[ 4847.747295] eth1: Tx timeout - resetting
[ 4850.034611] eth1: Tx timeout - resetting
[ 4852.062453] eth1: Tx timeout - resetting
[ 4854.353732] eth1: Tx timeout - resetting
[ 4856.641042] eth1: Tx timeout - resetting
[ 4858.932399] eth1: Tx timeout - resetting
[ 4861.223659] eth1: Tx timeout - resetting
[ 4863.514948] eth1: Tx timeout - resetting
[ 4865.510871] eth1: Tx timeout - resetting
[ 4867.802256] eth1: Tx timeout - resetting
[ 4870.021723] eth1: Tx timeout - resetting
[ 4872.304912] eth1: Tx timeout - resetting
[ 4874.304814] eth1: Tx timeout - resetting
[ 4876.596121] eth1: Tx timeout - resetting
[ 4878.659896] eth1: Tx timeout - resetting
[ 4880.815470] eth1: Tx timeout - resetting
[ 4883.106795] eth1: Tx timeout - resetting
[ 4885.398065] eth1: Tx timeout - resetting
[ 4887.445870] eth1: Tx timeout - resetting
[ 4889.737170] eth1: Tx timeout - resetting
[ 4891.733114] eth1: Tx timeout - resetting
[ 4893.765003] eth1: Tx timeout - resetting
[ 4895.784779] eth1: Tx timeout - resetting
[ 4897.780692] eth1: Tx timeout - resetting
[ 4899.776597] eth1: Tx timeout - resetting
[ 4902.067928] eth1: Tx timeout - resetting
[ 4904.067799] eth1: Tx timeout - resetting
[ 4906.359139] eth1: Tx timeout - resetting
[ 4908.642457] eth1: Tx timeout - resetting
[ 4910.933759] eth1: Tx timeout - resetting
[ 4912.949623] eth1: Tx timeout - resetting
[ 4915.061234] eth1: Tx timeout - resetting
[ 4917.352543] eth1: Tx timeout - resetting
[ 4919.639852] eth1: Tx timeout - resetting
[ 4921.931390] eth1: Tx timeout - resetting
[ 4924.218464] eth1: Tx timeout - resetting
[ 4926.509762] eth1: Tx timeout - resetting
[ 4928.553596] eth1: Tx timeout - resetting
[ 4930.561534] eth1: Tx timeout - resetting
[ 4932.601360] eth1: Tx timeout - resetting
[ 4934.609161] eth1: Tx timeout - resetting
[ 4936.900515] eth1: Tx timeout - resetting
[ 4939.191822] eth1: Tx timeout - resetting
[ 4941.475086] eth1: Tx timeout - resetting
[ 4943.766441] eth1: Tx timeout - resetting
[ 4946.057710] eth1: Tx timeout - resetting
[ 4948.173348] eth1: Tx timeout - resetting
[ 4950.368854] eth1: Tx timeout - resetting
[ 4952.656165] eth1: Tx timeout - resetting
[ 4954.883603] eth1: Tx timeout - resetting
[ 4957.174899] eth1: Tx timeout - resetting
[ 4959.466256] eth1: Tx timeout - resetting
[ 4961.573882] eth1: Tx timeout - resetting
[ 4963.569786] eth1: Tx timeout - resetting
[ 4965.857077] eth1: Tx timeout - resetting
[ 4967.888985] eth1: Tx timeout - resetting
[ 4970.180238] eth1: Tx timeout - resetting
[ 4972.467540] eth1: Tx timeout - resetting
[ 4974.758905] eth1: Tx timeout - resetting
[ 4977.046142] eth1: Tx timeout - resetting

cat /var/log/Xorg.0.log:
(II) RADEON(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) RADEON(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) RADEON(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(II) RADEON(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(II) RADEON(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) RADEON(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(II) RADEON(0): EDID vendor "SAM", prod id 263
(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 0
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: SAM  Model: 107  Serial#: 1279602999
(II) RADEON(0): Year: 2004  Week: 24
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 31  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 94.5 MHz   Image Size:  312 x 234 mm
(II) RADEON(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RADEON(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 71 kHz, PixClock max 110 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HVDX609893
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff004c2d07013731454c
(II) RADEON(0):         180e0103681f17782eee91a3544c9926
(II) RADEON(0):         0f5054bfee806159455931598180714f
(II) RADEON(0):         010101010101ea240060410028303060
(II) RADEON(0):         130038ea1000001e000000fd0032a01e
(II) RADEON(0):         470b000a202020202020000000fc0053
(II) RADEON(0):         796e634d61737465720a2020000000ff
(II) RADEON(0):         00485644583630393839330a202000fc
(II) RADEON(0): Output VGA-0 connected
in RADEONProbeOutputModes
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: SAM  Model: 107  Serial#: 1279602999
(II) RADEON(0): Year: 2004  Week: 24
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 31  vert.: 23
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 94.5 MHz   Image Size:  312 x 234 mm
(II) RADEON(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RADEON(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 71 kHz, PixClock max 110 MHz
(II) RADEON(0): Monitor name: SyncMaster
(II) RADEON(0): Serial No: HVDX609893
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff004c2d07013731454c
(II) RADEON(0):         180e0103681f17782eee91a3544c9926
(II) RADEON(0):         0f5054bfee806159455931598180714f
(II) RADEON(0):         010101010101ea240060410028303060
(II) RADEON(0):         130038ea1000001e000000fd0032a01e
(II) RADEON(0):         470b000a202020202020000000fc0053
(II) RADEON(0):         796e634d61737465720a2020000000ff
(II) RADEON(0):         00485644583630393839330a202000fc
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) RADEON(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) RADEON(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) RADEON(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(II) RADEON(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(II) RADEON(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(II) RADEON(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) RADEON(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(II) RADEON(0): EDID vendor "SAM", prod id 263
(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 0
(II) RADEON(0): Detected Monitor Type: 0
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video

glxinfo
root@ziv-desktop:/home/ziv# glxinfo
name of display: :0.0
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x26 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x28 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x29 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2b 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2e 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x30 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x31 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x32 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x64 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

fglrxinfo:
root@ziv-desktop:/home/ziv# fglrxinfo
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

BTW, i did all the commands BEFORE i disabled the effects, if its matter

---

### Post by malfist on 2007-11-24
What's up with all the timeouts on eth1?

---

### Post by gmaniac on 2007-11-24
You seem to have all sort of problems.
Grub a chair and listen ;)
First the output of dmesg is flooded by an error about your network card.
You should fix this or try the command from a reboot to see if anything else is wrong since although it's a problem i don't know if it could really slow you down.

Second you seem to be using the radeon driver but have installed the propriatery ones:confused:. This must be the problem you are having. 
I must leave now but i hope someone in here could help you further.
You could try and find a guide for the correct installation of the ati drivers.
Hope this got you started.
bye.

---

### Post by zivxx on 2007-11-24
i really got no idea, im pretty much new to linux

Edit: thanks gmaniac, check the post anyway when you come back..
ima try and look in google for clues

Second Edit: if it matter, i have 2 network cards and just one is in use, and a house-net router is connected to it and to that router there is another wireless router connected

---

### Post by zivxx on 2007-11-24
about the driver, i downloaded the driver from ati.amd,com
and i downloaded the driver for linux_86->radeon-> radeon x300(wich is my graphic card)

---

