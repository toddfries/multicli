The purpose of this utility is to provide one cli app that accesses a few key
bits in many different remote accounts, systems, etc.

Multi CLI aka multiple personality cli app.

Currently supporting:

* Hetzner .. shows server status (and soonest cancel date) plus cheapest server market server matching a preset of criteria
* namecheap .. domain status (id/expiration/name)
* voipms .. balance and subaccount registry status
* c1360 .. capitalone360.com ofx api to show accounts, balances, recent transactions
* coinbase .. BTC/USD price and wallet balance total
* kraken .. BTC/USD market price data
* bitstamp .. BTC/USD market price data
* bci .. last BTC block status
* bw .. bw.com info, not functional yet
* btcusd .. queries kraken+bitstamp+coinbase and valid results are pooled for a self made average BTC/USD 
* weather .. uses an api key to query the wunderground.org api for current and historic conditions


Example:

```
$ mcli -p weather
Sun/Moon rise->set 07:25->18:03 / 00:00->11:22
Temp(F) 30.9 :   0   1   2   3   4   5   6   7   8   9  10  11  12
       Temp(F)  29  27  27  23  22  22  21  21  21  23  26  30  33
     WindSpeed  10  10  10  10  10  10  10  10  11  12  11  11  10
     WindChill  19  17  17  13  10  10  10  10  10  11  17  21  26
      Humidity  50  53  55  67  68  67  66  66  65  58  52  46  40
  Rainfall(in) 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0

          Hour  13  14  15  16  17  18  19  20  21  22  23   0   1
       Temp(F)  37  39  41  42  41  37  34  33  31  30  30  30  30
     WindSpeed   9   8   7   6   5   4   4   5   6   6   5   6   6
     WindChill  31  34  36  39  38  34  30  29  24  24  25  24  24
      Humidity  34  32  30  30  31  37  43  47  51  53  54  55  56
  Rainfall(in) 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0 0.0


                Temp    Wind  RealFeel      POP  Rain
    Date       Hi/  Lo Hi/Lo   Hi/ Lo Humid.  %  (in) Conditions
Feb  6, 2018   32/  20 12/-10   32/   7  58    0  0.00 Partly Cloudy
Feb  7, 2018   43/  28 15/ 9   37/  16  43    0  0.00 Clear
Feb  8, 2018   59/  38 20/12   59/  27  34    0  0.00 Clear
Feb  9, 2018   63/  30 15/ 9   63/  19  46    0  0.00 Clear
Feb 10, 2018   42/  18 20/ 8   37/   1  52   20  0.00 Overcast
Feb 11, 2018   37/  23 25/13   28/   6  43   20  0.00 Partly Cloudy
Feb 12, 2018   50/  34 15/ 9   46/  24  33    0  0.00 Partly Cloudy
Feb 13, 2018   54/  28 20/ 6   54/  14  55   10  0.00 Clear
Feb 14, 2018   48/  32 15/ 5   45/  21  52   10  0.00 Partly Cloudy
Feb 15, 2018   57/  35 20/ 6   57/  23  44   10  0.00 Partly Cloudy
$
```

or

```
$ mcli -p weather -H 20010911               
20010911 00:00:00  82/ 55
  Date     Time   Temp   Press wspd  hum rain/hail/snow Remarks
20010911 00:53:00 64.00  30.23  8.1  58% 0 0 0 AO2 SLP237 T01780094 10256 20161 402720100 50001 $
20010911 01:53:00 63.00  30.22  8.1  63% 0 0 0 AO2 SLP232 T01720100 $
20010911 02:53:00 57.00  30.22  3.5  74% 0 0 0 AO2 SLP231 T01390094 $
20010911 03:53:00 57.00  30.21  4.6  72% 0 0 0 AO2 SLP230 T01390089 56007 $
20010911 04:53:00 57.00  30.21  3.5  72% 0 0 0 AO2 SLP228 T01390089 $
20010911 05:53:00 55.00  30.22  4.6  80% 0 0 0 AO2 SLP231 T01280094 $
20010911 06:53:00 55.90  30.23  4.6  75% 0 0 0 AO2 SLP235 T01330089 10178 20128 53004 $
20010911 07:53:00 55.90  30.25  3.5  80% 0 0 0 AO2 SLP241 T01330100
20010911 08:53:00 66.00  30.25  3.5  65% 0 0 0 AO2 SLP241 T01890122
20010911 09:53:00 72.00  30.25  9.2  53% 0 0 0 AO2 SLP242 T02220122 51008
20010911 10:53:00 75.00  30.25 10.4  53% 0 0 0 AO2 SLP242 T02390139
20010911 11:53:00 75.90  30.23  8.1  52% 0 0 0 AO2 SLP236 T02440139
20010911 12:53:00 78.10  30.21 10.4  50% 0 0 0 AO2 SLP230 T02560144 10261 20122 58011
20010911 13:53:00 79.00  30.19  9.2  48% 0 0 0 AO2 SLP221 T02610144
20010911 14:53:00 81.00  30.15  6.9  45% 0 0 0 AO2 SLP210 T02720144
20010911 15:53:00 81.00  30.13  6.9  44% 0 0 0 AO2 SLP201 T02720139 58028
20010911 16:53:00 82.00  30.11 10.4  42% 0 0 0 AO2 SLP196 T02780139
20010911 17:53:00 81.00  30.11  9.2  42% 0 0 0 AO2 SLP194 T02720133
20010911 18:53:00 80.10  30.10 10.4  43% 0 0 0 AO2 SLP193 T02670133 10278 20250 56009
20010911 19:53:00 75.00  30.11  8.1  50% 0 0 0 AO2 SLP194 T02390128 $
20010911 20:53:00 73.90  30.11  8.1  53% 0 0 0 AO2 SLP194 T02330133 $
20010911 21:53:00 73.00  30.11  9.2  53% 0 0 0 AO2 SLP196 T02280128 53005 $
20010911 22:53:00 72.00  30.10 10.4  55% 0 0 0 AO2 SLP193 T02220128 $
20010911 23:53:00 71.10  30.10 12.7  57% 0 0 0 AO2 SLP192 T02170128 $
```
