# মাস্টারিং এ্যারে

আমরা ডাটাটাইপ চ্যাপ্টারে প্রথম এ্যারে এর সাথে পরিচিত হই । পিএইচপিতে এ্যারে খুবই গুরুত্বপূর্ন কনসেপ্টগুলোর মধ্যে অন্যতম । এই চ্যাপ্টারে তাই আমরা এ্যারে সংশ্লিষ্ট বিষয়গুলো দেখবো ।

## ডিফাইনিং এ্যারে

ডাটা টাইপ চ্যাপ্টারে আমরা এ্যারে কিভাবে ডিফাইন করতে হয় তা দেখেছি । আবারো একবার দ্রুত দেখে নেই:

### এ্যাসোসিয়েটিভ এ্যারে

এই এ্যারেতে একটা কি \(key\) এর বিপরীতে একটা ভ্যালু স্টোর করা হয় ।

```php
<?php
$array = array(
    "foo" => "bar",
    "bar" => "foo",
);

// PHP 5.4 থেকে শর্টহ্যান্ড ব্যবহার করা যায় 
$array = [
    "foo" => "bar",
    "bar" => "foo",
];
?>
```

### ইনডেক্সেড এ্যারে

এখানে আমরা কোন কি ডিফাইন করি না । পিএইচপি নিজে থেকেই ক্রমিক সংখ্যা ব্যবহার করে ইনডেক্স এর জন্য ।

```php
<?php
$array = array("foo", "bar", "hello", "world");
var_dump($array);
```

### মিক্সড এ্যারে

এ ধরণের এ্যারে তে একই সাথে আমরা অটো ইনডেক্স এর পাশাপাশি নিজেদের প্রয়োজনীয় কি ডিফাইন করে দেই । যেমন:

```php
<?php
$array = array(23, 87, 32, "name" => "masnun", 43);
```

এখানে পিএইচপি প্রথম ৩টি আইটেমের ক্ষেত্রে ইন্টিজার ব্যবহার করবে । `name` কি টি স্ট্রিং । এরপর আবার পরের আইটেমটির জন্য আগের ইন্টিজার ভ্যালুর পরবর্তী ক্রমিক সংখ্যাটি ব্যবহার করবে ।

### কুইক নোটস

* এ্যারে তে লাস্ট আইটেম এর পর কমা দেওয়া অপশনাল । তবে মাল্টিলাইনে শেষ লাইনের শেষে কমা দেওয়া রিকমন্ডেড । 
* এ্যারের ভ্যালু যে কোন টাইপ হতে পারে । কিন্তু কি \(key\) এর টাইপ অবশ্যই স্ট্রিং অথবা ইন্টিজার হতে হবে । 
* কি এর টাইপ যদি স্ট্রিং হয় এবং ঐ স্ট্রিং যদি ভ্যালিড ইন্টিজারে কনভার্ট করা সম্ভব হয় তাহলে পিএইচপি ঐ কি এর টাইপ অটোমেটিক্যালি ইন্টিজার করে ফেলে । অর্থাৎ আপনার কি যদি হয় `"3"` তাহলে পিএইচপি ওটাকে `3` এ কনভার্ট করে ব্যবহার করবে । 
* ফ্লোটিং পয়েন্ট নাম্বার কিংবা বুলিয়ান হলে সেটা ইন্টিজারে কনভার্ট করে নেয় অনুরূপভাবে । 
* Null হলে সেটা এম্পটি স্ট্রিং এ পরিবর্তন করে নিবে । 
* অন্য কিছু কি হিসেবে ব্যবহার করতে গেলে Illegal key offset এরর পাওয়া যাবে । 
* কি \(key\) অপশনাল । যদি কি এর কোন ভ্যালু না দেওয়া হয় তাহলে পিএইচপি আগে ব্যবহার করা সবচেয়ে বড় ইন্টিজার কি এর ভ্যালু এক বাড়িয়ে নতুন কি তৈরি করে নেয় । কোন ইন্টিজার কি না থাকলে শূন্য থেকে শুরু করে । ইনডেক্সেড এ্যারে তে আমরা একই ঘটনা দেখেছি । 
* * এ্যারে গুলো জিরো বেইজড ইনডেক্স ব্যবহার করে । অর্থাৎ কি ডিফাইন না করে দিলে, প্রথম কি এর ভ্যালু হয় `0` । এরপর প্রতিবার এক এক করে বাড়ে । 

উদাহরণ:

```php
<?php
$array = array(
    1    => "a",
    "1"  => "b",
    1.5  => "c",
    true => "d",
);
var_dump($array);
```

## এ্যাক্সেসিং এ্যারে

আমরা এ্যারে ডিফাইন করলাম। এবার ব্যবহার করার পালা । এ্যারে থেকে কোন এলিমেন্ট এর ভ্যালু পাওয়ার জন্য সেটার কি \(key\) দিয়ে আমরা নিচের মত করে এ্যাক্সেস করতে পারি:

```php
<?php
<?php
$array = array(
    "foo" => "bar",
    42    => 24,
    "multi" => array(
         "dimensional" => array(
             "array" => "foo"
         )
    )
);

var_dump($array["foo"]);
var_dump($array[42]);
var_dump($array["multi"]["dimensional"]["array"]);
```

অর্থাৎ, এ্যারের ভ্যারিয়েবল এর পর থার্ড ব্রাকেটে আমরা কি পাস করি । `$array["foo"]` থেকে আমরা `$array` এর `foo` কি এর ভ্যালু পাই । আমরা এই উদাহরনে দেখছি এ্যারের ভিতরে আমরা আরো এ্যারে তৈরি করতে পারি । যে এ্যারের ভিতরে আরো এ্যারে থাকে সেটাকে আমরা মাল্টি ডাইমেনশনাল এ্যারে বলি । মাল্টি ডাইমেনশনাল এ্যারের ক্ষেত্রে আমরা প্রথমে একটি কি এর ভ্যালু বের করে নেই । সেটিও যদি এ্যারে হয় তবে পুনরায় আবার সেটির কি দিয়ে সংশ্লিষ্ট ভ্যালু বের করতে পারি ।

ইনডেক্সড এ্যারের ক্ষেত্রে কি গুলোর ভ্যালু নিউমেরিক অর্থাৎ ইন্টিজার হয় । আমরা জানি এই ইনডেক্স শুরু হয় শূন্য থেকে । প্রথম আইটেমটি তাই আমরা পাই `$array[0]` তে । এভাবে অন্যান্য আইটেমগুলিও আমরা তাদের নিজ নিজ ইনডেক্স ব্যবহার করে এ্যাক্সেস করা যায় । মিক্সড এ্যারের ক্ষেত্রে নিউমেরিক কি গুলো ইন্টিজার ভ্যালু ও স্ট্রিং কি গুলো তাদের স্ট্রিং ভ্যালু ব্যবহার করে এ্যাক্সেস করা হয় ।

মজার ব্যাপার হলো থার্ড ব্রাকেট এর পরিবর্তে আমরা সেকেন্ড ব্রাকেটও ব্যবহার করতে পারি । এটা ট্রাই করে দেখুন:

```php
<?php
$array = array(1,2,3);
var_dump($array{1});
```

এই যে কি দিয়ে কোন এ্যারে থেকে ঐ কি এর ভ্যালু এ্যাক্সেস করা - এটাকে ডিরেফারেন্সিং বলা হয় ।

পিএইচপি 5.4 থেকে আমরা সরাসরি ফাংশন থেকে রিটার্ন করা এ্যারে এ্যাক্সেস করতে পারি:

```php
<?php
function getArray() {
    return array(1, 2, 3);
}

// on PHP 5.4
$secondElement = getArray()[1];
```

এখানে আমরা `getArray()` এর ভ্যালু হিসেবে একটি এ্যারে পাই এবং সাথে সাথে আমরা সেটা ডিরেফারেন্স করছি । পিএইচপির আগের ভার্সন গুলোতে আমরা সরাসরি এভাবে ডিরেফারেন্স করতে পারতাম না । তখন আমাদের করতে হত নিচের মত করে:

```php
<?php
$tmp = getArray();
$secondElement = $tmp[1];
```

অর্থাৎ ফাংশন এর রিটার্ন ভ্যালু প্রথমে একটি ভ্যারিয়েবল এ স্টোর করে নিয়ে তারপর সেই ভ্যারিয়েবল থেকে ভ্যালু বের করতে হত ।

## এ্যারে মডিফাই করা

আমরা এ্যারে তে নতুন আইটেম যোগ করতে পারি, এক্সিস্টিং আইটেম এর ভ্যালু পরিবর্তন করতে পারি কিংবা পারি কোন আইটেম ডিলিট করে দিতে । আসুন দেখি এগুলো কিভাবে করা যায়:

### নতুন আইটেম যোগ করা

কি সহ যোগ করা:

```php
<?php

$array['key_name'] = 'val';
```

এক্ষেত্রে আমরা থার্ড ব্রাকেট এ কি এর নাম দিয়ে দেই এবং সাথে সাথে ভ্যালু ও এ্যাসাইন করি ।

কি ছাড়া যোগ করা:

```php
<?php

$array[] = "value";
```

এখানে আমরা কি এর কোন নাম দেইনি । সরাসরি ভ্যালু এ্যাসাইন করেছি । এক্ষেত্রে পিএইচপি ঐ এ্যারের ইন্টিজার কি গুলোর মধ্যে সবচেয়ে যেটা বড় তার পরের ইন্টিজার ভ্যালু টা কি হিসেবে ব্যবহার করবে । যেমন:

```php
<?php

$array = array("name" => "masnun", 23 => 'blah');
$array[] = 'aha';
var_dump($array);
```

এখানে সবচেয়ে বড় ইন্টিজার কি এর ভ্যালু ছিলো `23`, তাই `aha` এর কি হবে `24` \(23 + 1\) । এ্যারে ইনডেক্সিং এর ক্ষেত্রে পিএইচপির এই বিহ্যাভিয়র টা আমাদের মনে রাখা জরুরী ।

### ভ্যালু পরিবর্তন করা

কি দিয়ে এ্যাক্সেস করে আমরা একটি এলিমেন্ট পাই । ঐ এলিমেন্ট এর ভ্যালু আমরা নতুন করে এ্যাসাইন করতে পারি যেমন করে আমরা ভ্যারিয়েবল এর মান পরিবর্তন করি ।

```php
<?php
$array = array("name" => "masnun"); 
$array['name'] = "new name";
```

এখানে আমরা `name` কি এর ভ্যালু পরিবর্তন করে দিলাম । ইনডেক্সেড এ্যারের ক্ষেত্রেও ঠিক একইভাবে আমরা ভ্যালু পরিবর্তন করি তাদের নিউমেরিক ইনডেক্স ব্যবহার করে:

```php
<?php 
$array = array(100, 233, 456);
$array[1] = 21;
```

এখানে আমরা ২য় আইটেমটির ভ্যালু পরিবর্তন করে দিলাম ।

## এ্যারে থেকে আইটেম রিমুভ করা

আমরা `unset` ফাংশনটি ব্যবহার করে ভ্যারিয়েবল রিমুভ করে থাকি । এটা এ্যারের উপরও একইভাবে কাজ করে কেননা এ্যারেও মূলত ভ্যারিয়েবল এরই কালেকশন । এ্যারে থেকে একটা আইটেম রিমুভ করতে আমরা তার কি সহ এই ফাংশনটি কল করি:

```php
<?php

unset($array[3]);
```

আমরা সম্পূর্ণ এ্যারে ধরে ডিলিট করে দিতে চাইলে সরাসরি ঐ এ্যারেটি এই ফাংশনে পাস করে দিবো -

```php
<?php

unset($array);
```

খেয়াল রাখতে হবে, `unset` শুধু ঐ কি এবং তার ভ্যালুই রিমুভ করবে । কিন্তু এ্যারে টা রি-ইনডেক্স করবে না । মানে আপনি যদি ৩য় আইটেমটি মুছে ফেলেন, তাহলেও ৪র্থ আইটেমটির ইনডেক্স `3` ই থাকবে, এক কমে `2` হয়ে যাবে না । অর্থাৎ ৪র্থ আইটেমটি ৩য় আইটেমের স্থানে সরে আসবে না । আমাদের যদি একটা আইটেম রিমুভ করার পর এই ভ্যালুগুলো পুনরায় ইনডেক্স করার প্রয়োজন হয় তবে আমরা `array_values` ফাংশন ব্যবহার করতে পারি ।

এ্যারে সংশ্লিষ্ট বেশ কিছু প্রয়োজনীয় ফাংশন দেখবো আমরা পরবর্তী চ্যাপ্টারে ।

