---
title: "monitors going blank randomly"
date: 2014-05-04
forum: General Help
---

### Post by thegoodinn on 2014-05-04
Hi,
I have HP laptop on docking station with two external monitors and since installing 14.04 I've noticed that monitors are randomly going to sleep. This lasts for a second and then they both come back to life. This doesn't happen in Win7 which is on dual boot.
For the life of me I can't figure out what is going on so I'm attaching Xorg and dmesg entries that coincide with the events in hope someone can provide an answer. Let me know if you need any additional information.
Thanks!

dmesg:
[ 3858.528896] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3858.528923] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3858.528939] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3858.528947] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3858.528960] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3858.528973] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3858.528985] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3858.528997] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3858.529004] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3858.529016] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3858.529028] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3858.529040] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3858.544707] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3858.544715] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3858.544719] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3858.544722] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3858.544728] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3858.544734] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3858.544741] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3858.544747] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3858.544749] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3858.544755] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3858.544761] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3858.544767] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3858.604880] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3858.604898] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3858.604910] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3858.604917] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3858.604930] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3858.604943] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3858.604955] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3858.604967] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3858.604974] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3858.604986] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3858.604998] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3858.605010] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3858.620852] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3858.620870] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3858.620882] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3858.620889] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3858.620901] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3858.620914] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3858.620934] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3858.620947] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3858.620954] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3858.620967] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3858.620979] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3858.620992] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3868.064907] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3868.064934] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3868.064951] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3868.064958] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3868.064971] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3868.064984] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3868.064996] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3868.065009] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3868.065016] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3868.065027] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3868.065040] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3868.065052] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3868.080867] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3868.080891] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3868.080905] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3868.080913] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3868.080926] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3868.080939] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3868.080951] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3868.080964] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3868.080970] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3868.080982] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3868.080995] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3868.081007] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3868.424894] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3868.424919] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3868.424934] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3868.424941] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3868.424954] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3868.424967] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3868.424980] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3868.424992] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3868.424998] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3868.425010] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3868.425022] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3868.425034] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3868.440850] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3868.440868] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3868.440880] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3868.440887] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3868.440900] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3868.440912] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3868.440925] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3868.440937] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3868.440943] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3868.440955] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3868.440967] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3868.440979] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3868.456860] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3868.456879] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3868.456890] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3868.456898] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3868.456910] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3868.456923] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3868.456935] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3868.456947] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3868.456954] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3868.456966] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3868.456978] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3868.456990] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3868.472869] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3868.472885] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3868.472896] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3868.472903] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3868.472915] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3868.472928] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3868.472941] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3868.472953] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3868.472959] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3868.472971] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3868.472983] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3868.472996] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3868.488896] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3868.488918] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3868.488933] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3868.488940] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3868.488953] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3868.488966] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3868.488978] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3868.488990] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3868.488996] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3868.489008] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3868.489020] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3868.489032] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3868.504476] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3868.504490] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3868.504498] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3868.504502] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3868.504508] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3868.504515] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3868.504521] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3868.504528] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3868.504530] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3868.504537] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3868.504543] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3868.504549] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3868.520905] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3868.520924] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3868.520936] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3868.520943] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3868.520956] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3868.520968] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3868.520981] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3868.520993] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3868.520999] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3868.521011] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3868.521023] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3868.521035] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3868.810727] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3868.810742] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3868.810751] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3868.810755] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3868.810763] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3868.810770] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3868.810778] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3868.810785] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3868.810789] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3868.810796] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3868.810803] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3868.810811] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3868.828856] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3868.828873] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3868.828885] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3868.828892] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3868.828904] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3868.828917] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3868.828929] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3868.828941] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3868.828948] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3868.828959] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3868.828972] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3868.828984] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3869.180666] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3869.180686] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3869.180698] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3869.180703] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3869.180712] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3869.180721] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3869.180730] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3869.180740] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3869.180744] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3869.180752] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3869.180761] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3869.180770] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3869.505951] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3869.505965] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3869.505973] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3869.505976] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3869.505983] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3869.505989] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3869.505996] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3869.506002] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3869.506005] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3869.506011] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3869.506018] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3869.506024] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3887.516899] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3887.516924] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3887.516941] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3887.516949] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3887.516961] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3887.516974] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3887.516986] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3887.516999] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3887.517005] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3887.517017] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3887.517029] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3887.517041] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3887.532833] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3887.532850] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3887.532861] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3887.532868] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3887.532881] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3887.532894] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3887.532906] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3887.532918] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3887.532925] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3887.532936] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3887.532949] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3887.532961] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]
[ 3897.444503] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[ 3897.444518] lpc_ich 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[ 3897.444528] yenta_cardbus 0000:02:06.0: CardBus bridge to [bus 03]
[ 3897.444532] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5000-0x50ff]
[ 3897.444540] yenta_cardbus 0000:02:06.0:   bridge window [io  0x5400-0x54ff]
[ 3897.444547] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[ 3897.444555] yenta_cardbus 0000:02:06.0:   bridge window [mem 0xc8000000-0xcbffffff]
[ 3897.444563] yenta_cardbus 0000:02:06.1: CardBus bridge to [bus 04-07]
[ 3897.444566] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5800-0x58ff]
[ 3897.444573] yenta_cardbus 0000:02:06.1:   bridge window [io  0x5c00-0x5cff]
[ 3897.444581] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xc4000000-0xc7ffffff pref]
[ 3897.444588] yenta_cardbus 0000:02:06.1:   bridge window [mem 0xcc000000-0xcfffffff]

Xorg:
[  3896.689] (II) intel(0): switch to mode 1280x1024@60.0 on VGA1 using  pipe 0, position (1280, 0), rotation normal, reflection none
[  3896.762] (II) intel(0): switch to mode 1280x1024@60.0 on DVI1 using  pipe 1, position (0, 0), rotation normal, reflection none
[   3898.167] (II) intel(0): switch to mode 1280x1024@60.0 on VGA1 using  pipe 0, position (1280, 0), rotation normal, reflection none
[  3898.202] (II) intel(0): switch to mode 1280x1024@60.0 on DVI1 using  pipe 1, position (0, 0), rotation normal, reflection none

---

