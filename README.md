laravel-collect

## Usage

### User Model

```
use Illuminate\Foundation\Auth\User as Authenticatable;
use Vetor\Laravel\Collect\Collector\Models\Traits\Collector;
use Vetor\Contracts\Collect\Collector\Models\Collector as CollectorContract;

class User extends Authenticatable implements CollectorContract
{
    use Collector;
}
```

### Article Model

```
use Vetor\Laravel\Collect\Collectable\Models\Traits\Collectable;
use Vetor\Contracts\Collect\Collectable\Models\Collectable as CollectableContract;

class Article extends Model implements CollectableContract
{
    use Collectable;
}
```

### Available Methods

#### User

// 收藏

$user->collect($article);

// 取消收藏

$user->cancelCollect($article);

// 用户的所有收藏记录

$user->collections;

// 用户收藏的文章记录

$user->collectionsWhereCollectable(Article::class);

#### Article

// 收藏

$article->collect();

// 取消收藏

$article->cancelCollect();

> 注：默认为当前用户，可以把用户实例作为参数传入。


//  获取文章的收藏情况

$article->collections();

// 获取文章收藏数

$article->collections_count;

// 根据收藏数排序

Article::orderByCollectionsCount()->get();

> 注：升序 'asc'；降序 'desc'；默认为升序。

#### Collection

// 获取收藏表里所有文章

Collection::whereCollectable(Article::class)->get();
