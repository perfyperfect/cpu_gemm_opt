# gemm_opt

optimize gemm on x86 arch, tested on **Intel(R) Xeon(R) Gold 6142** CPU, single core
* L1d cache:             32K
* L1i cache:             32K
* L2 cache:              1024K
* L3 cache:              22528K


```
# 6x16 micro kernel

freq: 2600.0MHz, theoritical: 81.250 gflops (avx256,fmadd)
MC:516, NC:4096, KC:256, MR:6, NR:16
require: L1:16.0KB(KC*NR*4), L2:516.0KB(KC*MC*4), L3:4096.0KB(KC*NC*4)
    M    N    K alpha beta   gflops(%)   gflops_ref(%)
   48   48   48  1.0  1.0  59.19(72.8493)  28.35(34.8978)
   96   96   96  1.0  1.0  70.88(87.2359)  56.64(69.7096)
  144  144  144  1.0  1.0  74.40(91.5714)  64.67(79.5967)
  192  192  192  1.0  1.0  75.62(93.0763)  68.08(83.7963)
  240  240  240  1.0  1.0  75.45(92.8598)  69.86(85.9850)
  288  288  288  1.0  1.0  71.81(88.3813)  70.28(86.4970)
  384  384  384  1.0  1.0  73.19(90.0760)  71.46(87.9538)
  480  480  480  1.0  1.0  74.25(91.3881)  73.56(90.5334)
  576  576  576  1.0  1.0  74.19(91.3149)  74.79(92.0507)
  768  768  768  1.0  1.0  75.44(92.8462)  71.79(88.3620)
  960  960  960  1.0  1.0  76.39(94.0135)  75.79(93.2845)
 1152 1152 1152  1.0  1.0  75.66(93.1188)  75.03(92.3449)
 1344 1344 1344  1.0  1.0  76.15(93.7270)  74.61(91.8315)
 1536 1536 1536  1.0  1.0  74.82(92.0805)  71.99(88.5983)
 1728 1728 1728  1.0  1.0  75.17(92.5204)  73.98(91.0536)
 1920 1920 1920  1.0  1.0  75.24(92.6033)  73.52(90.4919)
 2112 2112 2112  1.0  1.0  73.42(90.3600)  73.55(90.5247)
 2496 2496 2496  1.0  1.0  69.41(85.4307)  73.50(90.4670)
 2880 2880 2880  1.0  1.0  65.83(81.0228)  73.27(90.1816)
 3264 3264 3264  1.0  1.0  64.93(79.9167)  73.22(90.1117)
 3648 3648 3648  1.0  1.0  64.85(79.8198)  73.00(89.8508)
 4032 4032 4032  1.0  1.0  66.05(81.2979)  72.51(89.2383)
 4416 4416 4416  1.0  1.0  65.13(80.1606)  72.69(89.4590)
 4800 4800 4800  1.0  1.0  65.04(80.0490)  73.00(89.8518)
 5184 5184 5184  1.0  1.0  63.92(78.6669)  72.71(89.4844)
 5568 5568 5568  1.0  1.0  64.30(79.1384)  72.87(89.6839)
 5952 5952 5952  1.0  1.0  63.69(78.3823)  72.82(89.6261)


```