# BLS_API PACKAGE
## Introduction:
    - This package is design to get aggregated data from Bureau Labor of Statistics
    rather than specifying the Series Id.
    - The package already have the series scraped and defined.
## Installation:
### Pip:
You can use pip to install this package
```bash
pip install bls_api
```
## Usage:
### Labor Force data:
Let's first interact with Labor Force data in BLS
```python
from bls_api import labor_force

### Initiate the instance
instance=labor_force()
### if you have the token from BLS you can set it up if not it is not the problem.
instance.token="<Your Token>"

"""
Let's assume we have 2 series LAUMT531338000000006 and LAUMT531338000000005
We want to get data from these 2 series.
These series belongs to labor_force_participation_data
Let's these 2 series to the instance
"""
custom_series=instance.add_custom_series(["LAUMT531338000000006","LAUMT531338000000005"])

### add_custom_series returns a series_object class
### Now we can set the _from and _to to this object class
custom_series._from=2017
custom_series._to=2018
### now we can loop through the custom series to get the data:
for data_ in custom_series:
    print(data_)
"""
Output:
{'seriesID': 'LAUMT531338000000006', 'year': '2018', 'period': 'M12', 'periodName': 'December', 'value': '115622', 'area': 'Bellingham, WA Metropolitan Sta
tistical Area', 'area_type': 'Metropolitan areas', 'region': 'Washington'}
{'seriesID': 'LAUMT531338000000006', 'year': '2018', 'period': 'M11', 'periodName': 'November', 'value': '115397', 'area': 'Bellingham, WA Metropolitan Sta
tistical Area', 'area_type': 'Metropolitan areas', 'region': 'Washington'}
{'seriesID': 'LAUMT531338000000006', 'year': '2018', 'period': 'M10', 'periodName': 'October', 'value': '114589', 'area': 'Bellingham, WA Metropolitan Stat
istical Area', 'area_type': 'Metropolitan areas', 'region': 'Washington'}
....
....
....
"""

### If you  want to get all the available series in Labor_Force
all_series=instance.add_all_series()
all_series._from=2017
all_series._to=2018

for data_ in all_series:
    print(data_)

"""
Output:
{'seriesID': 'LAUMT531338000000006', 'year': '2018', 'period': 'M12', 'periodName': 'December', 'value': '115622', 'area': 'Bellingham, WA Metropolitan Sta
tistical Area', 'area_type': 'Metropolitan areas', 'region': 'Washington'}
{'seriesID': 'LAUMT531338000000006', 'year': '2018', 'period': 'M11', 'periodName': 'November', 'value': '115397', 'area': 'Bellingham, WA Metropolitan Sta
tistical Area', 'area_type': 'Metropolitan areas', 'region': 'Washington'}
{'seriesID': 'LAUMT531338000000006', 'year': '2018', 'period': 'M10', 'periodName': 'October', 'value': '114589', 'area': 'Bellingham, WA Metropolitan Stat
istical Area', 'area_type': 'Metropolitan areas', 'region': 'Washington'}
{'seriesID': 'LAUMT531338000000006', 'year': '2018', 'period': 'M09', 'periodName': 'September', 'value': '110890', 'area': 'Bellingham, WA Metropolitan St
atistical Area', 'area_type': 'Metropolitan areas', 'region': 'Washington'}

....
....
....
....

"""  

```
## License 
MIT License

Copyright (c) 2022 Tien Nguyen

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
