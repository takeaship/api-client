# Online Judge API Client

[![test](https://github.com/kmyk/online-judge-api-client/workflows/test/badge.svg)](https://github.com/kmyk/online-judge-api-client/actions)
[![Documentation Status](https://readthedocs.org/projects/online-judge-api-client/badge/?version=master)](https://online-judge-api-client.readthedocs.io/en/master/)
[![PyPI](https://img.shields.io/pypi/v/online-judge-api-client.svg)](https://pypi.python.org/pypi/online-judge-api-client)
[![PyPI](https://img.shields.io/pypi/l/online-judge-api-client.svg)](https://github.com/kmyk/online-judge-api-client/blob/master/LICENSE)


## What is this?

This is an API client for various online judges, used as the backend library of [`oj` command](https://github.com/kmyk/online-judge-tools).
You can use the Python library (`onlinejudge` module) and the command-line interface (`oj-api` command) which talks JSON compatible with [jmerle/competitive-companion](https://github.com/jmerle/competitive-companion).


## How to install

**CAUTION: under developping; this may work stably, but all public APIs are unstable**

``` console
$ git clone https://github.com/kmyk/online-judge-api-client
$ cd online-judge-api-client
$ pip3 install -e .
```


## Supported websites

| website                                                                        | get sample cases   | get system cases   | get metadata       | get contest data   | login service      | submit code        |
|--------------------------------------------------------------------------------|--------------------|--------------------|--------------------|--------------------|--------------------|--------------------|
| [Aizu Online Judge](https://onlinejudge.u-aizu.ac.jp/home)                     | :heavy_check_mark: | :heavy_check_mark: |                    |                    | :white_check_mark: |                    |
| [Anarchy Golf](http://golf.shinh.org/)                                         | :heavy_check_mark: | :white_check_mark: |                    |                    | :white_check_mark: |                    |
| [AtCoder](https://atcoder.jp/)                                                 | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [CodeChef](https://www.codechef.com/)                                          | :heavy_check_mark: |                    |                    |                    | :white_check_mark: |                    |
| [Codeforces](https://codeforces.com/)                                          | :heavy_check_mark: |                    | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [CS Academy](https://csacademy.com/)                                           | :heavy_check_mark: |                    |                    |                    | :white_check_mark: |                    |
| [Facebook Hacker Cup](https://www.facebook.com/hackercup/)                     | :heavy_check_mark: |                    |                    |                    | :white_check_mark: |                    |
| [Google Code Jam](https://codingcompetitions.withgoogle.com/codejam)           | :heavy_check_mark: |                    |                    |                    | :white_check_mark: |                    |
| [Google Kick Start](https://codingcompetitions.withgoogle.com/kickstart)       | :heavy_check_mark: |                    |                    |                    | :white_check_mark: |                    |
| [HackerRank](https://www.hackerrank.com/)                                      | :white_check_mark: | :heavy_check_mark: |                    |                    | :white_check_mark: | :heavy_check_mark: |
| [Kattis](https://open.kattis.com/)                                             | :heavy_check_mark: |                    |                    |                    | :white_check_mark: |                    |
| [Library Checker](https://judge.yosupo.jp/)                                    | :heavy_check_mark: | :heavy_check_mark: |                    |                    | :white_check_mark: |                    |
| [PKU JudgeOnline](http://poj.org/)                                             | :heavy_check_mark: |                    |                    |                    | :white_check_mark: |                    |
| [Sphere Online Judge](https://www.spoj.com/)                                   | :heavy_check_mark: |                    |                    |                    | :white_check_mark: |                    |
| [Toph](https://toph.co/)                                                       | :heavy_check_mark: |                    |                    |                    | :white_check_mark: | :heavy_check_mark: |
| [yukicoder](https://yukicoder.me/)                                             | :heavy_check_mark: | :heavy_check_mark: |                    |                    | :white_check_mark: | :heavy_check_mark: |


## Examples

``` json
$ oj-api get-problem https://atcoder.jp/contests/arc100/tasks/arc100_b | jq .result
{
  "url": "https://atcoder.jp/contests/arc100/tasks/arc100_b",
  "name": "Equal Cut",
  "context": {
    "contest": {
      "name": "AtCoder Regular Contest 100",
      "url": "https://atcoder.jp/contests/arc100"
    },
    "alphabet": "D"
  },
  "memoryLimit": 1024,
  "timeLimit": 2000,
  "tests": [
    {
      "input": "5\n3 2 4 1 2\n",
      "output": "2\n"
    },
    {
      "input": "10\n10 71 84 33 6 47 23 25 52 64\n",
      "output": "36\n"
    },
    {
      "input": "7\n1 2 3 1000000000 4 5 6\n",
      "output": "999999994\n"
    }
  ]
}
```

``` json
$ oj-api get-problem --compatibility https://atcoder.jp/contests/arc100/tasks/arc100_b | jq .result
{
  "name": "D. Equal Cut",
  "group": "AtCoder Regular Contest 100",
  "url": "https://atcoder.jp/contests/arc100/tasks/arc100_b",
  "interactive": false,
  "memoryLimit": 1024,
  "timeLimit": 2000,
  "tests": [
    {
      "input": "5\n3 2 4 1 2\n",
      "output": "2\n"
    },
    {
      "input": "10\n10 71 84 33 6 47 23 25 52 64\n",
      "output": "36\n"
    },
    {
      "input": "7\n1 2 3 1000000000 4 5 6\n",
      "output": "999999994\n"
    }
  ],
  "testType": "single",
  "input": {
    "type": "stdin"
  },
  "output": {
    "type": "stdout"
  },
  "languages": {
    "java": {
      "mainClass": "Main",
      "taskClass": "Task"
    }
  }
}
```

``` json
$ oj-api get-contest https://atcoder.jp/contests/arc100 | jq .result
{
  "url": "https://atcoder.jp/contests/arc100",
  "name": "AtCoder Regular Contest 100",
  "problems": [
    {
      "url": "https://atcoder.jp/contests/arc100/tasks/arc100_a",
      "name": "Linear Approximation",
      "context": {
        "contest": {
          "name": "AtCoder Regular Contest 100",
          "url": "https://atcoder.jp/contests/arc100"
        },
        "alphabet": "C"
      }
    },
    {
      "url": "https://atcoder.jp/contests/arc100/tasks/arc100_b",
      "name": "Equal Cut",
      "context": {
        "contest": {
          "name": "AtCoder Regular Contest 100",
          "url": "https://atcoder.jp/contests/arc100"
        },
        "alphabet": "D"
      }
    },
    {
      "url": "https://atcoder.jp/contests/arc100/tasks/arc100_c",
      "name": "Or Plus Max",
      "context": {
        "contest": {
          "name": "AtCoder Regular Contest 100",
          "url": "https://atcoder.jp/contests/arc100"
        },
        "alphabet": "E"
      }
    },
    {
      "url": "https://atcoder.jp/contests/arc100/tasks/arc100_d",
      "name": "Colorful Sequences",
      "context": {
        "contest": {
          "name": "AtCoder Regular Contest 100",
          "url": "https://atcoder.jp/contests/arc100"
        },
        "alphabet": "F"
      }
    }
  ]
}
```
