# i2s-busModbus
Código do barramento servidor Modbus


# **BARRAMENTO MODBUS**

<br>
___
<br>
# **Instalação no Debian usuário picg**

```
cd /home/picg
su -
apt install initscript python-pymodbus
exit
cd
git clone http://gitlab.nc2.iff.edu.br/i2s/busModbus.git
mkdir /home/picg/logs

Edit /etc/rc.local e inclua as linhas

> /home/picg/busModbus.log
/home/picg/busModbus/busModbus.py 2> /home/picg/logs/busModbus.log &

reiniciar o servidor e testar

```

# **Endereçamento modbus**
```
0 ~ 49 Inversores Fronius (solar)
50 ~ 99 Inversores Ginlong (eólico)
100 ~ 199 Medidores de consumo de energia
200 ~ 219 Medidores de vazão de água valores instantâneo e totalizado
220 ~ 269 Valores de vazão totalizada dia, mês e anos dos medidores de vazão
300 ~ 399 Cálculos do rendimento, economia e outros
400 ~ 449 Conectividade e diagnósticos


VAZÃO TOTALIZADA DIA, MÊS E ANO DOS MEDIDORES DE VAZÃO - NODE-RED
#220 ~ 269

220 DAY_VOLUME parte alta em m3 FIT101
221 DAY_VOLUME parte baixa em m3  FIT101
222 MONTH_VOLUME parte alta em m3  FIT101
223 MONTH_VOLUME parte baixa em m3  FIT101
224 YEAR_VOLUME parte alta em m3  FIT101
225 YEAR_VOLUME parte baixa em m3  FIT101
TOTAL_VOLUME nos endereços originais  FIT101 MB 202 203
230 DAY_VOLUME parte alta em m3 FIT102
231 DAY_VOLUME parte baixa em m3  FIT102
232 MONTH_VOLUME parte alta em m3  FIT102
233 MONTH_VOLUME parte baixa em m3  FIT102
234 YEAR_VOLUME parte alta em m3  FIT102
235 YEAR_VOLUME parte baixa em m3  FIT102
TOTAL_VOLUME nos endereços originais  FIT102 MB 206 207
240 DAY_VOLUME parte alta em m3 FIT103
241 DAY_VOLUME parte baixa em m3  FIT103
242 MONTH_VOLUME parte alta em m3  FIT103
243 MONTH_VOLUME parte baixa em m3  FIT103
244 YEAR_VOLUME parte alta em m3  FIT103
245 YEAR_VOLUME parte baixa em m3  FIT103
TOTAL_VOLUME nos endereços originais  FIT103 MB 210 211
250 DAY_VOLUME parte alta em m3 FIT104
251 DAY_VOLUME parte baixa em m3  FIT104
252 MONTH_VOLUME parte alta em m3  FIT104
253 MONTH_VOLUME parte baixa em m3  FIT104
254 YEAR_VOLUME parte alta em m3  FIT104
255 YEAR_VOLUME parte baixa em m3  FIT104
TOTAL_VOLUME nos endereços originais  FIT104 MB 214 215
260 DAY_VOLUME parte alta em m3 FIT105
261 DAY_VOLUME parte baixa em m3  FIT105
262 MONTH_VOLUME parte alta em m3  FIT105
263 MONTH_VOLUME parte baixa em m3  FIT105
264 YEAR_VOLUME parte alta em m3  FIT105
265 YEAR_VOLUME parte baixa em m3  FIT105
TOTAL_VOLUME nos endereços originais  FIT105 MB 218 219


CÁLCULOS DO RENDIMENTO, ECONOMIA E OUTROS - NODE-RED
#300 ~ 349 Cálculos do rendimento, economia e outros

300 geracaoTotalEnergy parte alta em Wh
301 geracaoTotalEnergy parte baixa
302 rendimentoTotalEnergy parte alta em R$
303 rendimentoTotalEnergy parte baixa
304 geracaoYearEnergy parte alta em W
305 geracaoYearEnergy parte baixa
306 rendimentoYearEnergy parte alta em R$
307 rendimentoYearEnergy parte baixa
308 geracaoMonthEnergy parte alta em Wh
309 geracaoMonthEnergy parte baixa
310 rendimentoMonthEnergy parte alta em R$
311 rendimentoMonthEnergy parte baixa
312 geracaoDayEnergy parte alta em Wh
313 geracaoDayEnergy parte baixa
314 rendimentoDayEnergy parte alta em R$
315 rendimentoDayEnergy parte baixa
316 economiaTotalTonCO2 parte alta
317 economiaTotalTonCO2 parte baixa
318 economiaTotalArvores parte alta
319 economiaTotalArvores parte baixa
320 consumoPACEnergy parte alta em W
321 consumoPACEnergy parte baixa em W
322 consumoDayEnergy parte alta em Wh
323 consumoDayEnergy parte baixa em Wh
324 consumoMonthEnergy parte alta em Wh
325 consumoMonthEnergy parte baixa em Wh
326 consumoYearEnergy parte alta em Wh
327 consumoYearEnergy parte baixa em Wh
328 consumoTotalEnergy parte alta em Wh
329 consumoTotalEnergy parte baixa em Wh
330 consumoDayWater BLOCO A parte baixa em m3
331 consumoDayWater BLOCO A parte alta em m3
332 consumoMonthWater BLOCO A parte baixa em m3
333 consumoMonthWater BLOCO A parte alta em m3
334 consumoYearWater BLOCO A parte baixa em m3
335 consumoYearWater BLOCO A parte alta em m3
336 consumoTotalWater BLOCO A parte baixa em m3
337 consumoTotalWater BLOCO A parte alta em m3
338
339
340 rendimentoTotalWater parte alta em R$
341 rendimentoTotalWater parte baixa
341
342
343
344
345
346
347
348
349
350
351
352
353
354
355
356
357
358
359
360
361
362
363
364
365
366
367
368
369
370
371
372
373
374
375
376
377
378
379
380
381
382
383
384
385
386
387
388
389
390
391
392
393
394
395
396
397
398
399

CONECTIVIDADE E DISGNÓSTICO - NODE-RED
400 ~ 449 Conectividade e diagnósticos

valor do bit: 1 ativo, 0 inativo

400
   bit 0 - 10.80.0.88 inversor Fronius 1
   bit 1 - 10.80.0.88 inversor Fronius 2
   bit 2 - 10.80.0.88 inversor Fronius 3
   bit 3 - 10.80.0.88 inversor Fronius 4
   bit 4 - 10.80.0.84 inversor Fronius 5
   bit 5 - 10.80.0.27 inversor Ginlong 1
   bit 6 - 10.80.0.27 inversor Ginlong 2
   bit 7 - RESERVADO
   bit 8 - RESERVADO
   bit 9 - RESERVADO
   bit 10 - RESERVADO
   bit 11 - RESERVADO
   bit 12 - RESERVADO
   bit 13 - RESERVADO
   bit 14 - RESERVADO
   bit 15 - RESERVADO
401
   bit 0 - 10.80.0.110 medidor de energia 1 bloco A
   bit 1 - 10.80.0.111 medidor de energia 2 bloco A
   bit 2 - 10.80.0.112 medidor de energia 3 bloco A
   bit 3 - 10.80.0.113 medidor de energia 1 bloco B
   bit 4 - 10.80.0.114 medidor de energia 2 bloco B
   bit 5 - 10.80.0.115 medidor de energia 3 bloco B
   bit 6 - 10.80.0.116 medidor de energia 1 bloco C
   bit 7 - 10.80.0.117 medidor de energia 2 bloco C
   bit 8 - 10.80.0.118 medidor de energia 3 bloco C
   bit 9 - 10.80.0.119 medidor de energia 1 bloco Guarita
   bit 10 - 10.80.0.120 medidor de energia 2 bloco Guarita
   bit 11 - 10.80.0.121 medidor de energia 3 bloco Guarita
   bit 12 - 10.80.0.122 medidor de energia 1 oficina
   bit 13 - 10.80.0.123 medidor de energia 2 oficina
   bit 14 - 10.80.0.124 medidor de energia 3 oficina
   bit 15 - 10.80.0.125 medidor de energia 1 área externa
402
   bit 0 - 10.80.0.126 medidor de energia 2 área externa
   bit 1 - 10.80.0.127 medidor de energia 3 área externa
   bit 2 - RESERVADO
   bit 3 - RESERVADO
   bit 4 - RESERVADO
   bit 5 - RESERVADO
   bit 6 - RESERVADO
   bit 7 - RESERVADO
   bit 8 - RESERVADO
   bit 9 - RESERVADO
   bit 10 - RESERVADO
   bit 11 - RESERVADO
   bit 12 - RESERVADO
   bit 13 - RESERVADO
   bit 14 - RESERVADO
   bit 15 - RESERVADO
403
   bit 0 - 10.80.0.129 controlador ETA
   bit 1 - 10.80.0.130 medidor de vazão ETA
   bit 2 - 10.80.0.131 medidor de vazão bloco A
   bit 3 - 10.80.0.132 medidor de vazão bloco B
   bit 4 - 10.80.0.133 medidor de vazão bloco C
   bit 5 - 10.80.0.133 medidor de vazão bloco guarita
   bit 6 - RESERVADO
   bit 7 - RESERVADO
   bit 8 - RESERVADO
   bit 9 - RESERVADO
   bit 10 - RESERVADO
   bit 11 - RESERVADO
   bit 12 - RESERVADO
   bit 13 - RESERVADO
   bit 14 - RESERVADO
   bit 15 - RESERVADO
   



```
