# Shot Chart
> Python module to plot NBA shot chart data and distributions for players and teams and some utilities.


This file will become your README and also the index of your documentation.

## Install

`pip install shot_chart`

## How to use

We first create a pandas dataframe from the source data.

```
shots_2019 = make_df(untar_data(URLs.SHOTS_2019))
```

## Listing teams for the season

```
list_teams(shots_2019)
```




    0            Atlanta
    1            Orlando
    183       Sacramento
    184             Utah
    341         Oklahoma
    343     Golden State
    511           Denver
    512      New Orleans
    675        Milwaukee
    1016        Portland
    1224         Phoenix
    1226        Brooklyn
    1412     San Antonio
    1413         Memphis
    1934         Toronto
    2119    Philadelphia
    2296       Minnesota
    2477       LA Lakers
    2655         Houston
    2656     LA Clippers
    2843       Charlotte
    3017          Boston
    3018      Washington
    3383         Detroit
    3918           Miami
    5020       Cleveland
    5535         Indiana
    6407        New York
    6410         Chicago
    8473          Dallas
    Name: team, dtype: object



## Listing players who took at least 1 shot for a particular team

```
list_team_players(shots_2019, 'Portland')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>shots_by</th>
      <th>count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>CJ McCollum</td>
      <td>1212</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Damian Lillard</td>
      <td>1158</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Carmelo Anthony</td>
      <td>678</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Hassan Whiteside</td>
      <td>676</td>
    </tr>
    <tr>
      <th>0</th>
      <td>Anfernee Simons</td>
      <td>522</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Gary Trent</td>
      <td>349</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Kent Bazemore</td>
      <td>322</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Mario Hezonja</td>
      <td>188</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Rodney Hood</td>
      <td>172</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Trevor Ariza</td>
      <td>159</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Nassir Little</td>
      <td>151</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Skal Labissière</td>
      <td>147</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Anthony Tolliver</td>
      <td>117</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Caleb Swanigan</td>
      <td>43</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Jaylen Hoard</td>
      <td>32</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Wenyen Gabriel</td>
      <td>29</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Zach Collins</td>
      <td>19</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Moses Brown</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>



## Plotting team shot distribution

```
houston = TeamShots(shots_2019,"Houston")
```

```
houston.plot_shots()
```


![png](docs/images/output_12_0.png)


```
houston.plot_shots(date_range=((2020,1,3), (2020,1,11)))
```


![png](docs/images/output_13_0.png)


Please check the extra options when using the plotting functions

```
portland_20191125 = TeamShots(shots_2019,"Portland")
```

```
portland_20191125.list_game_ids(2019,11,25)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>game_id</th>
      <th>winner</th>
      <th>loser</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>45560</th>
      <td>201911250CHI</td>
      <td>Portland</td>
      <td>Chicago</td>
    </tr>
  </tbody>
</table>
</div>



```
portland_20191125.plot_shots("201911250CHI")
```


![png](docs/images/output_17_0.png)


## Plotting player shot distribution

```
player_shots = PlayerShots(shots_2019,"Anthony Davis")
```

```
player_shots.plot_shots()
```


![png](docs/images/output_20_0.png)


```
dlo = PlayerShots(shots_2019,"D'Angelo Russell")
```

```
dlo.plot_shots()
```


![png](docs/images/output_22_0.png)


```
dlo.plot_shots(distance_limit=(16,26),attempt="2-pointer")
```


![png](docs/images/output_23_0.png)


```
dlo.plot_effective(most_or_least="most")
```


![png](docs/images/output_24_0.png)


```
dlo.plot_effective(most_or_least="most",exclude=["0ft"])
```


![png](docs/images/output_25_0.png)


```
dlo.plot_effective(most_or_least="most",min_shots="auto",exclude=['2ft'])
```


![png](docs/images/output_26_0.png)


```
dlo.plot_effective(most_or_least="least")
```


![png](docs/images/output_27_0.png)


```
dlo.plot_effective(most_or_least="least",min_shots="auto")
```


![png](docs/images/output_28_0.png)

