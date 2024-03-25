# TIOBE Index Historical Data

## Parsing

### 2001 Era

```js
(() => {
    const format = (data, delimiter='\t') => data.map(row => row.join(delimiter)).join('\n');
    const getFilename = (path) => path.split('/').pop();
    const parseImg = (img) => {
        switch (img) {
            case 'Same.gif': return 0;
            case 'Plus.gif': return 1;
            case 'Min.gif': return -1;
        }
    }
    const parseImgArr = (imgArr) => imgArr.reduce((total, img) => total + parseImg(img), 0);
    const data = [...document.querySelectorAll('table[align="center"] tbody tr')].map(tr => {
        return [...tr.querySelectorAll('td, th')].map(cell => {
            const imgArr = [...(cell.querySelectorAll('img') ?? [])].map(img => getFilename(img.src));
            return imgArr.length ? parseImgArr(imgArr) : cell.textContent.trim();
        });
    });
    console.log(format(data));
})();
```

## See

- <https://web.archive.org/web/20010815064939/http://www.tiobe.com/tpci.htm>
- <https://web.archive.org/web/20010901000000*/https://www.tiobe.com>

## See also

- <https://github.com/toUpperCase78/tiobe-index-ratings/blob/master/tiobe_index_april2023.csv>
- <https://www.tiobe.com/tiobe-index/python/>